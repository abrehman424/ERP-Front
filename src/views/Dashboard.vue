<template>
  <div class="relative w-full min-h-screen px-2 sm:px-4 lg:px-6 py-3 sm:py-4">
    <!-- Subtle Background Effects -->
    <!-- <div class="absolute left-0 bottom-0 w-[500px] h-[400px] bg-gradient-to-r from-purple-400/10 to-pink-400/10 blur-3xl rounded-full z-0 pointer-events-none"></div>
    <div class="absolute right-0 top-0 w-[400px] h-[300px] bg-gradient-to-r from-blue-400/10 to-cyan-400/10 blur-3xl rounded-full z-0 pointer-events-none"></div>
     -->
    <!-- Compact Header Section -->
    <!-- <div class="relative z-10 mb-4 rounded-2xl border border-gray-200/60 bg-white/90 backdrop-blur-xl px-4 sm:px-6 py-4 shadow-sm">
      <div class="flex flex-col lg:flex-row justify-between items-start lg:items-center gap-4">
        <div class="header-content flex-1">
          <div class="flex items-center gap-2 mb-2">
            <div class="relative">
              <div class="w-2 h-2 bg-green-500 rounded-full"></div>
            </div>
            <span class="text-[10px] sm:text-xs text-green-600 font-medium">System Online</span>
          </div>
          <h1 class="text-lg sm:text-xl font-bold text-gray-900 tracking-tight mb-1">
            Good {{ timeOfDay }}, 
            <span class="bg-gradient-to-r from-purple-600 to-pink-600 bg-clip-text text-transparent">{{ userName }}</span>
          </h1>
          <p class="text-gray-500 text-xs mb-3">{{ greetingMessage }}</p>
          <div class="flex flex-wrap items-center gap-2 sm:gap-3">
            <div class="flex items-center gap-1.5 text-[10px] sm:text-xs text-gray-600 bg-gray-50 px-2 py-1 rounded-md">
              <IconClock :size="12" class="text-indigo-600" stroke-width="2" />
              <span class="font-medium">{{ currentTime }}</span>
            </div>
            <div class="flex items-center gap-1.5 text-[10px] sm:text-xs text-gray-600 bg-gray-50 px-2 py-1 rounded-md">
              <IconCalendar :size="12" class="text-indigo-600" stroke-width="2" />
              <span class="font-medium">{{ currentDate }}</span>
            </div>
          </div>
        </div>
        <div class="flex items-center gap-2 w-full sm:w-auto">
          <button 
            @click="refreshData" 
            :disabled="refreshing" 
            class="flex items-center justify-center gap-1.5 h-9 px-4 rounded-lg bg-gradient-to-r from-blue-600 to-purple-600 text-white text-xs font-semibold shadow-sm hover:shadow-md transition-all duration-200 hover:scale-105 active:scale-95 disabled:opacity-50 disabled:cursor-not-allowed"
          >
            <IconRefresh :size="14" :class="refreshing ? 'animate-spin' : ''" stroke-width="2" />
            <span>{{ refreshing ? 'Refreshing...' : 'Refresh' }}</span>
          </button>
          <button 
            @click="exportReport" 
            class="flex items-center justify-center gap-1.5 h-9 px-4 rounded-lg bg-gradient-to-r from-green-600 to-emerald-600 text-white text-xs font-semibold shadow-sm hover:shadow-md transition-all duration-200 hover:scale-105 active:scale-95"
          >
            <IconDownload :size="14" stroke-width="2" />
            <span>Export</span>
          </button>
        </div>
      </div>
    </div> -->


    <div class="flex items-center justify-between mb-6">
      <!-- Title -->
      <div>
        <h2 class="text-xl font-semibold text-slate-900">
          Analytics Overview
        </h2>
        <p class="text-sm text-slate-500">
          Welcome back, {{ userName }}. Here's what's happening today.
        </p>
      </div>

      <!-- Filters -->
      <div class="flex items-center gap-2 bg-white p-1 rounded-full shadow-sm border text-[#475569] font-bold">

        <!-- Last 30 Days -->
        <button @click="setPeriod('30')" :class="[
          'px-4 py-2 text-sm rounded-full transition',
          selectedPeriod === '30' ? 'bg-indigo-600 text-white' : 'text-slate-600 hover:bg-slate-100'
        ]">
          Last 30 Days
        </button>

        <button @click="setPeriod('quarter')" :class="[
          'px-4 py-2 text-sm rounded-full transition',
          selectedPeriod === 'quarter' ? 'bg-indigo-600 text-white' : 'text-slate-600 hover:bg-slate-100'
        ]">
          This Quarter
        </button>

        <button @click="setPeriod('ytd')" :class="[
          'px-4 py-2 text-sm rounded-full transition',
          selectedPeriod === 'ytd' ? 'bg-indigo-600 text-white' : 'text-slate-600 hover:bg-slate-100'
        ]">
          Year to Date
        </button>

        <!-- Calendar -->
        <div class="relative font-bold">
          <button @click="mainDateFilter.startDate = mainDateFilter.startDate ? '' : true"
            class="flex items-center gap-1 text-[#475569] p-2 rounded-full hover:bg-slate-100 transition ">
            <svg width="11" height="12" viewBox="0 0 11 12" fill="none" xmlns="http://www.w3.org/2000/svg">
              <path
                d="M9.32422 1.14844C9.65234 1.14844 9.92578 1.26693 10.1445 1.50391C10.3815 1.72266 10.5 1.99609 10.5 2.32422V10.5C10.5 10.8099 10.3815 11.0833 10.1445 11.3203C9.92578 11.5391 9.65234 11.6484 9.32422 11.6484H1.17578C0.847656 11.6484 0.565104 11.5391 0.328125 11.3203C0.109375 11.0833 0 10.8099 0 10.5V2.32422C0 1.99609 0.109375 1.72266 0.328125 1.50391C0.565104 1.26693 0.847656 1.14844 1.17578 1.14844H1.75V0H2.92578V1.14844H7.57422V0H8.75V1.14844H9.32422ZM9.32422 10.5V4.64844H1.17578V10.5H9.32422ZM3.5 7V5.82422H2.32422V7H3.5ZM5.82422 7V5.82422H4.67578V7H5.82422ZM8.17578 7V5.82422H7V7H8.17578ZM3.5 9.32422V8.14844H2.32422V9.32422H3.5ZM5.82422 9.32422V8.14844H4.67578V9.32422H5.82422ZM8.17578 9.32422V8.14844H7V9.32422H8.17578Z"
                fill="#475569" />
            </svg>
            Custom
          </button>
          <!-- Calendar Popup -->
          <div v-if="mainDateFilter.startDate === true"
            class="absolute right-0 mt-2 bg-white rounded-xl shadow-lg border p-3 z-50">
            <CompactDatePicker @change="handleMainDateChange" />
          </div>
        </div>

      </div>
    </div>

    <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-4">

      <!-- Total Students -->
      <div
        class="relative overflow-hidden bg-white rounded-xl border border-[#ffffff] shadow p-4 flex flex-col justify-between">
        <div class="flex items-center space-x-2 justify-between">
          <div>
            <svg width="40" height="40" viewBox="0 0 40 40" fill="none" xmlns="http://www.w3.org/2000/svg">
              <rect width="40" height="40" rx="16" fill="#DBEAFE" />
              <path
                d="M23.9844 20.9844C24.8594 20.9844 25.8125 21.1094 26.8438 21.3594C27.875 21.6094 28.8281 22.0156 29.7031 22.5781C30.5781 23.1406 31.0156 23.7812 31.0156 24.5V26.9844H25.0156V24.5C25.0156 23.125 24.3594 21.9688 23.0469 21.0312C23.2656 21 23.5781 20.9844 23.9844 20.9844ZM13.1562 21.3594C14.1875 21.1094 15.1406 20.9844 16.0156 20.9844C16.8906 20.9844 17.8438 21.1094 18.875 21.3594C19.9062 21.6094 20.8438 22.0156 21.6875 22.5781C22.5625 23.1406 23 23.7812 23 24.5V26.9844H8.98438V24.5C8.98438 23.7812 9.42188 23.1406 10.2969 22.5781C11.1719 22.0156 12.125 21.6094 13.1562 21.3594ZM18.0781 18.125C17.5156 18.7188 16.8281 19.0156 16.0156 19.0156C15.2031 19.0156 14.5 18.7188 13.9062 18.125C13.3125 17.5312 13.0156 16.8281 13.0156 16.0156C13.0156 15.2031 13.3125 14.5 13.9062 13.9062C14.5 13.3125 15.2031 13.0156 16.0156 13.0156C16.8281 13.0156 17.5156 13.3125 18.0781 13.9062C18.6719 14.5 18.9688 15.2031 18.9688 16.0156C18.9688 16.8281 18.6719 17.5312 18.0781 18.125ZM26.0938 18.125C25.5 18.7188 24.7969 19.0156 23.9844 19.0156C23.1719 19.0156 22.4688 18.7188 21.875 18.125C21.2812 17.5312 20.9844 16.8281 20.9844 16.0156C20.9844 15.2031 21.2812 14.5 21.875 13.9062C22.4688 13.3125 23.1719 13.0156 23.9844 13.0156C24.7969 13.0156 25.5 13.3125 26.0938 13.9062C26.6875 14.5 26.9844 15.2031 26.9844 16.0156C26.9844 16.8281 26.6875 17.5312 26.0938 18.125Z"
                fill="#2563EB" />
            </svg>
          </div>
          <div class="flex items-center gap-1">
            <svg width="10" height="6" viewBox="0 0 10 6" fill="none" xmlns="http://www.w3.org/2000/svg">
              <path
                d="M6.98438 0H9.98438V3L8.83594 1.85156L5.69531 4.99219L3.70312 3L0.703125 6L0 5.29688L3.70312 1.59375L5.69531 3.58594L8.13281 1.14844L6.98438 0Z"
                fill="#10B981" />
            </svg>
            <p class="text-green-500 font-semibold text-sm">+12%</p>
          </div>
        </div>
        <div class="flex flex-col gap-2 pt-2">
          <p class="text-[#64748B] text-sm font-medium">Total Students</p>
          <p class="text-2xl font-bold text-[#0F172A]">12,450</p>
        </div>
        <div class="absolute bottom-0 right-0 opacity-2 pointer-events-none">
          <svg width="96" height="48" viewBox="0 0 96 48" fill="none" xmlns="http://www.w3.org/2000/svg">
            <g opacity="0.1">
              <g clip-path="url(#clip0_2_329)">
                <path d="M0 38.4C16 35.2 32 36.8 48 43.2C64 49.6 80 44.8 96 28.8" stroke="black" stroke-width="5.76" />
              </g>
            </g>
            <defs>
              <clipPath id="clip0_2_329">
                <rect width="96" height="48" fill="white" />
              </clipPath>
            </defs>
          </svg>
        </div>

      </div>

      <!-- Active Staff -->
      <div class="relative overflow-hidden bg-white rounded-xl shadow p-4 flex flex-col justify-between">
        <div class="flex items-center space-x-2 justify-between">
          <div>
            <svg width="40" height="40" viewBox="0 0 40 40" fill="none" xmlns="http://www.w3.org/2000/svg">
              <rect width="40" height="40" rx="16" fill="#F3E8FF" />
              <path
                d="M26 21.5V20H22.0156V21.5H26ZM26 24.5V23H22.0156V24.5H26ZM20.9844 17V11.9844H19.0156V17H20.9844ZM20 26V25.25C20 24.8125 19.6562 24.4531 18.9688 24.1719C18.2812 23.8906 17.625 23.75 17 23.75C16.375 23.75 15.7188 23.8906 15.0312 24.1719C14.3438 24.4531 14 24.8125 14 25.25V26H20ZM18.0781 20.4219C17.7969 20.1406 17.4375 20 17 20C16.5625 20 16.2031 20.1406 15.9219 20.4219C15.6406 20.7031 15.5 21.0625 15.5 21.5C15.5 21.9375 15.6406 22.2969 15.9219 22.5781C16.2031 22.8594 16.5625 23 17 23C17.4375 23 17.7969 22.8594 18.0781 22.5781C18.3594 22.2969 18.5 21.9375 18.5 21.5C18.5 21.0625 18.3594 20.7031 18.0781 20.4219ZM28.0156 14.9844C28.5469 14.9844 29 15.1875 29.375 15.5938C29.7812 16 29.9844 16.4688 29.9844 17V28.0156C29.9844 28.5469 29.7812 29.0156 29.375 29.4219C29 29.7969 28.5469 29.9844 28.0156 29.9844H11.9844C11.4531 29.9844 10.9844 29.7969 10.5781 29.4219C10.2031 29.0156 10.0156 28.5469 10.0156 28.0156V17C10.0156 16.4688 10.2031 16 10.5781 15.5938C10.9844 15.1875 11.4531 14.9844 11.9844 14.9844H17V11.9844C17 11.4531 17.2031 11 17.6094 10.625C18.0156 10.2188 18.4844 10.0156 19.0156 10.0156H20.9844C21.5156 10.0156 21.9844 10.2188 22.3906 10.625C22.7969 11 23 11.4531 23 11.9844V14.9844H28.0156Z"
                fill="#9333EA" />
            </svg>

          </div>
          <div class="flex items-center gap-1">
            <svg width="10" height="6" viewBox="0 0 10 6" fill="none" xmlns="http://www.w3.org/2000/svg">
              <path
                d="M6.98438 0H9.98438V3L8.83594 1.85156L5.69531 4.99219L3.70312 3L0.703125 6L0 5.29688L3.70312 1.59375L5.69531 3.58594L8.13281 1.14844L6.98438 0Z"
                fill="#10B981" />
            </svg>
            <p class="text-green-500 font-semibold text-sm">+12%</p>
          </div>
        </div>
        <div class="flex flex-col gap-2 pt-2">
          <p class="text-[#64748B] text-sm font-medium">Active Staff</p>
          <p class="text-2xl font-bold text-[#0F172A]">840</p>
        </div>

        <div class="absolute bottom-0 right-0 opacity-4.5 ">
          <svg width="96" height="48" viewBox="0 0 96 48" fill="none" xmlns="http://www.w3.org/2000/svg">
            <g opacity="0.1">
              <g clip-path="url(#clip0_2_341)">
                <path d="M0 43.2C16 40 32 33.6 48 24C64 14.4 80 9.60001 96 9.60001" stroke="black"
                  stroke-width="5.76" />
              </g>
            </g>
            <defs>
              <clipPath id="clip0_2_341">
                <rect width="96" height="48" fill="white" />
              </clipPath>
            </defs>
          </svg>
        </div>

      </div>

      <!-- Monthly Revenue -->
      <div class="relative bg-white rounded-2xl shadow p-4 overflow-hidden">

        <!-- Top Row -->
        <div class="flex justify-between items-start">
          <div>
            <!-- Icon SVG -->
            <svg width="40" height="40" viewBox="0 0 40 40" fill="none" xmlns="http://www.w3.org/2000/svg">
              <rect width="40" height="40" rx="16" fill="#D1FAE5" />
              <path
                d="M26.9844 22.0156C26.9844 22.5469 26.7812 23.0156 26.375 23.4219C26 23.7969 25.5469 23.9844 25.0156 23.9844H11C10.4375 23.9844 9.95312 23.7969 9.54688 23.4219C9.17188 23.0156 8.98438 22.5469 8.98438 22.0156V14C8.98438 13.4375 9.17188 12.9688 9.54688 12.5938C9.95312 12.1875 10.4375 11.9844 11 11.9844H25.0156C25.5469 11.9844 26 12.1875 26.375 12.5938C26.7812 12.9688 26.9844 13.4375 26.9844 14V22.0156ZM17.9844 20.9844C18.5469 20.9844 19.0469 20.8594 19.4844 20.6094C19.9531 20.3281 20.3125 19.9688 20.5625 19.5312C20.8438 19.0625 20.9844 18.5469 20.9844 17.9844C20.9844 17.4531 20.8438 16.9688 20.5625 16.5312C20.3125 16.0625 19.9531 15.6875 19.4844 15.4062C19.0469 15.125 18.5469 14.9844 17.9844 14.9844C17.4531 14.9844 16.9531 15.125 16.4844 15.4062C16.0469 15.6875 15.6875 16.0625 15.4062 16.5312C15.125 16.9688 14.9844 17.4531 14.9844 17.9844C14.9844 18.5469 15.125 19.0625 15.4062 19.5312C15.6875 19.9688 16.0469 20.3281 16.4844 20.6094C16.9531 20.8594 17.4531 20.9844 17.9844 20.9844ZM31.0156 14.9844H29V26H11.9844V28.0156H29C29.5625 28.0156 30.0312 27.8281 30.4062 27.4531C30.8125 27.0469 31.0156 26.5625 31.0156 26V14.9844Z"
                fill="#059669" />
            </svg>

          </div>

          <div class="flex items-center gap-1 text-red-500 font-semibold text-sm">
            <svg width="10" height="6" viewBox="0 0 10 6" fill="none" xmlns="http://www.w3.org/2000/svg">
              <path
                d="M6.98438 6L8.13281 4.85156L5.69531 2.41406L3.70312 4.40625L0 0.703125L0.703125 0L3.70312 3L5.69531 1.00781L8.83594 4.14844L9.98438 3V6H6.98438Z"
                fill="#F43F5E" />
            </svg>
            -5%
          </div>
        </div>

        <!-- Text Content -->
        <div class="flex flex-col gap-2 pt-4 align-middle">
          <p class="text-[#64748B] text-sm font-medium">Monthly Revenue</p>
          <p class="text-2xl font-bold text-[#0F172A]">$420,500</p>
        </div>

        <!-- Background Chart SVG -->
        <svg class="absolute right-0.5 bottom-0.5" width="96" height="48" viewBox="0 0 96 48" fill="none"
          xmlns="http://www.w3.org/2000/svg">
          <g opacity="0.1">
            <g clip-path="url(#clip0_2_353)">
              <path d="M0 9.60001C16 12.8 32 20.8 48 33.6C64 46.4 80 49.6 96 43.2" stroke="black" stroke-width="5.76" />
            </g>
          </g>
          <defs>
            <clipPath id="clip0_2_353">
              <rect width="96" height="48" fill="white" />
            </clipPath>
          </defs>
        </svg>


      </div>

      <!-- Avg Attendance -->
      <div class="relative overflow-hidden bg-white rounded-xl shadow p-4 flex flex-col justify-between">
        <div class="flex items-center space-x-2  justify-between">
          <div>
            <svg width="40" height="40" viewBox="0 0 40 40" fill="none" xmlns="http://www.w3.org/2000/svg">
              <rect width="40" height="40" rx="16" fill="#FEF3C7" />
              <path
                d="M28.0156 29V16.0156H11.9844V29H28.0156ZM28.0156 11C28.5469 11 29 11.2031 29.375 11.6094C29.7812 12.0156 29.9844 12.4844 29.9844 13.0156V29C29.9844 29.5312 29.7812 30 29.375 30.4062C29 30.8125 28.5469 31.0156 28.0156 31.0156H11.9844C11.4531 31.0156 10.9844 30.8125 10.5781 30.4062C10.2031 30 10.0156 29.5312 10.0156 29V13.0156C10.0156 12.4844 10.2031 12.0156 10.5781 11.6094C10.9844 11.2031 11.4531 11 11.9844 11H13.0156V8.98438H14.9844V11H25.0156V8.98438H26.9844V11H28.0156Z"
                fill="#D97706" />
            </svg>


          </div>
          <div class="flex items-center gap-1">
            <svg width="10" height="6" viewBox="0 0 10 6" fill="none" xmlns="http://www.w3.org/2000/svg">
              <path
                d="M6.98438 0H9.98438V3L8.83594 1.85156L5.69531 4.99219L3.70312 3L0.703125 6L0 5.29688L3.70312 1.59375L5.69531 3.58594L8.13281 1.14844L6.98438 0Z"
                fill="#10B981" />
            </svg>
            <p class="text-green-500 font-semibold text-sm">+0.8%</p>
          </div>
        </div>
        <div class="flex flex-col gap-2 pt-2">
          <p class="text-[#64748B] text-sm font-medium">Avg Attendance</p>
          <p class="text-2xl font-bold text-[#0F172A]">94.2%</p>
        </div>
        <div class="absolute bottom-0 right-0 opacity-2.5 pointer-events-none">
          <svg width="96" height="48" viewBox="0 0 96 48" fill="none" xmlns="http://www.w3.org/2000/svg">
            <g opacity="0.1">
              <g clip-path="url(#clip0_2_365)">
                <path d="M0 33.6C16 30.4 32 30.4 48 33.6C64 36.8 80 33.6 96 24" stroke="black" stroke-width="5.76" />
              </g>
            </g>
            <defs>
              <clipPath id="clip0_2_365">
                <rect width="96" height="48" fill="white" />
              </clipPath>
            </defs>
          </svg>
        </div>
      </div>
    </div>





    <!-- Compact Date Filter -->
    <!-- <div
      class="relative z-10 my-4 rounded-2xl border border-gray-200/60 bg-white/90 backdrop-blur-xl px-4 sm:px-5 py-3 shadow-sm">
      <div class="flex flex-col sm:flex-row justify-between items-start sm:items-center gap-3">
        <div class="flex items-center gap-2">
          <div class="w-8 h-8 rounded-lg bg-indigo-100 flex items-center justify-center">
            <IconCalendarEvent :size="16" class="text-indigo-600" stroke-width="2" />
          </div>
          <div>
            <h3 class="text-xs sm:text-sm font-semibold text-gray-900">Date Range Filter</h3>
            <p class="text-[10px] text-gray-500 hidden sm:block">Filter all dashboard data</p>
          </div>
        </div>
        <div class="flex flex-wrap items-center gap-2 w-full sm:w-auto">
          <CompactDatePicker v-model="mainDateFilter.startDate" placeholder="" @change="handleMainDateChange" />
          <button @click="clearMainDateFilter"
            class="h-7 px-3 rounded-lg bg-gray-100 hover:bg-gray-200 text-gray-700 text-[10px] font-medium transition-all duration-200 hover:scale-105 active:scale-95 border border-gray-200">
            Clear
          </button>
        </div>
      </div>
    </div> -->

    <!-- Compact Statistics Cards -->
    <!-- <div class="relative z-10 grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-3 sm:gap-4 mb-4">
      <StatCard v-for="(stat, index) in statisticsCards" :key="index" :stat="stat" @click="showStatDetails" />
    </div> -->


    <!-- Compact Charts Section -->
    <div class="relative z-10 grid grid-cols-1 lg:grid-cols-3 gap-4 pt-4">
      <!-- Charts -->
      <div class="lg:col-span-2 space-y-4">
        <!-- Compact Bar Chart -->
        <div
          class="relative overflow-hidden rounded-xl border border-[] bg-gradient-to-br from-white/90 to-white/70 backdrop-blur-xl p-4 sm:p-5 shadow-sm hover:shadow-md transition-all duration-300">
          <div class="flex flex-col sm:flex-row justify-between items-start sm:items-center gap-3 mb-4">
            <div>
              <h3 class="text-sm font-bold text-gray-900 mb-0.5">Monthly Income Overview</h3>
              <p class="text-[10px] text-gray-500">Actual vs Projected Revenue</p>
            </div>
            <div class="flex items-center gap-4 flex-wrap">

              <!-- Chart Type Dropdown - Right side below date -->
              <div class="relative">
                <select v-model="selectedChartType" @change="handleChartTypeChange"
                  class="h-7 rounded-lg border border-gray-200 bg-white px-3 pr-8 text-[10px] font-medium text-gray-900 focus:ring-2 focus:ring-indigo-500/20 focus:border-indigo-300 transition-all duration-200 appearance-none cursor-pointer hover:border-indigo-300 bg-[url('data:image/svg+xml,%3Csvg xmlns=\'http://www.w3.org/2000/svg\' width=\'12\' height=\'12\' viewBox=\'0 0 12 12\'%3E%3Cpath fill=\'%236366f1\' d=\'M6 9L2 5h8z\'/%3E%3C/svg%3E')] bg-no-repeat bg-[length:12px] bg-[position:calc(100%-0.5rem)_center] shadow-sm hover:shadow">
                  <option value="bar">Bar Chart</option>
                  <option value="line">Line Chart</option>
                  <option value="area">Area Chart</option>
                  <option value="doughnut">Doughnut Chart</option>
                  <option value="radar">Radar Chart</option>
                </select>
              </div>

              <div class="flex items-center gap-3 text-[10px]">
                <div class="flex items-center gap-1">
                  <span class="w-2 h-2 rounded-full bg-purple-600 inline-block"></span>
                  <span class="text-gray-500">Actual</span>
                </div>
                <div class="flex items-center gap-1">
                  <span class="w-2 h-2 rounded-full bg-gray-300 inline-block"></span>
                  <span class="text-gray-500">Projected</span>
                </div>
              </div>


              <!-- <select v-model="selectedPeriod" @change="updateChartData"
                class="h-7 rounded-lg border border-gray-200 bg-white px-2 pr-6 text-[10px] font-medium text-gray-900 focus:ring-2 focus:ring-indigo-500/20 focus:border-indigo-300 transition-all duration-200 appearance-none cursor-pointer hover:border-indigo-300 bg-[url('data:image/svg+xml,%3Csvg xmlns=\'http://www.w3.org/2000/svg\' width=\'10\' height=\'10\' viewBox=\'0 0 10 10\'%3E%3Cpath fill=\'%233b3b4f\' d=\'M5 7.35L1.65 4 2.35 3.3 5 5.95 7.65 3.3 8.35 4z\'/%3E%3C/svg%3E')] bg-no-repeat bg-[length:10px] bg-[position:calc(100%-0.5rem)_center] shadow-sm hover:shadow">
                <option value="6">6M</option>
                <option value="12">1Y</option>
                <option value="24">2Y</option>
              </select>
              <button @click="toggleChartView"
                class="h-7 w-7 rounded-lg border border-gray-200 bg-white flex items-center justify-center text-gray-500 hover:bg-indigo-50 hover:text-indigo-600 hover:border-indigo-300 transition-all duration-200 shadow-sm hover:shadow">
                <component :is="chartView === 'bar' ? IconChartLine : IconChartBar" :size="14" :stroke-width="2" />
              </button> -->

            </div>
          </div>
          <div class="h-64 relative">
            <ChartJsWrapper ref="incomeChart" :type="chartView" :data="incomeData" :options="incomeChartOptions"
              :loading="chartLoading" height="256px" />
          </div>
        </div>

        <!-- Compact Pie Chart -->

  <div
    class="group relative rounded-xl border border-gray-200/60 bg-white/90 p-5 sm:p-6 shadow-sm backdrop-blur-xl hover:shadow-lg transition-all duration-300 overflow-hidden"
  >
    <!-- Subtle animated gradient overlay on hover -->
    <div
      class="absolute inset-0 bg-gradient-to-br from-blue-50/0 via-indigo-50/0 to-purple-50/0 group-hover:from-blue-50/20 group-hover:via-indigo-50/15 group-hover:to-purple-50/20 transition-all duration-500 pointer-events-none"
    ></div>

    <div class="relative z-10">
      <!-- Header -->
      <div class="mb-5">
        <h3 class="text-lg font-bold text-gray-900">Fee Distribution</h3>
      </div>

      <!-- Chart Container -->
      <div class="flex flex-col items-center justify-center">
        <!-- Doughnut Chart with Center Label -->
        <div class="relative w-48 h-48 sm:w-56 sm:h-56 mx-auto">
          <HighchartsWrapper
            ref="feeChart"
            :options="feeChartOptions"
            :loading="false"
            height="100%"
          />

          <!-- Center Text Overlay (fallback / custom styling if Highcharts label not enough) -->
          <div
            class="absolute inset-0 flex flex-col items-center justify-center pointer-events-none"
          >
            <div class="text-4xl sm:text-5xl font-bold text-gray-900">100%</div>
            <div class="text-xs sm:text-sm text-gray-500 font-medium mt-1">Collected</div>
          </div>
        </div>

        <!-- Legend Below -->
        <div class="mt-6 w-full max-w-xs space-y-2.5">
          <div
            v-for="(item, index) in legendItems"
            :key="index"
            class="flex items-center justify-between text-sm"
          >
            <div class="flex items-center gap-2.5">
              <div
                class="w-3 h-3 rounded-full"
                :style="{ backgroundColor: item.color }"
              ></div>
              <span class="text-gray-700 font-medium">{{ item.label }}</span>
            </div>
            <span class="text-gray-600 font-semibold">{{ item.percent }}%</span>
          </div>
        </div>
      </div>
    </div>
  </div>


      </div>

      <!-- Compact Sidebar -->
      <div class="space-y-4 animate-fade-in-up" style="animation-delay: 500ms">
        <!-- Compact Recent Activities -->
        <div
          class="group relative rounded-xl border border-gray-200/60 bg-[#5B13EC] p-4 sm:p-5 shadow-sm backdrop-blur-xl hover:shadow-md transition-all duration-300 overflow-hidden">
          <!-- Animated gradient overlay on hover -->
          <div>
            <h1 class="text-2xl font-bold text-[#FFFFFF]">Quick Platform Stats</h1>
          </div>
          <div class="flex flex-col gap-3 py-3">
            <div class="flex p-3 gap-2.5 pt-4 shadow-sm rounded-2xl bg-[#FFFFFF1A]  ">
              <div class="flex items-center">
                <svg width="24" height="17" viewBox="0 0 24 17" fill="none" xmlns="http://www.w3.org/2000/svg">
                  <path
                    d="M9.98438 13.0312L16.5938 6.42188L15.1875 5.01562L9.98438 10.1719L7.92188 8.10938L6.51562 9.51562L9.98438 13.0312ZM19.3594 6.04688C20.6406 6.14062 21.7344 6.67188 22.6406 7.64062C23.5469 8.57812 24 9.70312 24 11.0156C24 12.3906 23.5 13.5781 22.5 14.5781C21.5312 15.5469 20.3594 16.0312 18.9844 16.0312H6C4.34375 16.0312 2.92188 15.4531 1.73438 14.2969C0.578125 13.1094 0 11.6875 0 10.0312C0 8.5625 0.515625 7.25 1.54688 6.09375C2.60938 4.90625 3.875 4.23438 5.34375 4.07812C6 2.85938 6.92188 1.875 8.10938 1.125C9.29688 0.375 10.5938 0 12 0C13.6875 0 15.25 0.59375 16.6875 1.78125C18.1562 2.96875 19.0469 4.39062 19.3594 6.04688Z"
                    fill="white" fill-opacity="0.7" />
                </svg>
              </div>

              <div class="flex justify-between items-center w-full">
                <div>
                  <p class="text-sm font-bold text-[#FFFFFFB2] ">Server Status</p>
                  <p class="text-sm font-bold text-[#FFFFFF] ">Operational</p>
                </div>
                <div class=" rounded-full  bg-[#34D399] w-2 h-2 inline-block "></div>
              </div>

            </div>

            <div class="flex p-3 gap-2.5 pt-4 shadow-sm rounded-2xl bg-[#FFFFFF1A]  ">
              <div class="flex items-center">
                <svg width="20" height="17" viewBox="0 0 20 17" fill="none" xmlns="http://www.w3.org/2000/svg">
                  <path
                    d="M18 4.03125V2.01562L9.98438 7.03125L1.96875 2.01562V4.03125L9.98438 9L18 4.03125ZM18 0C18.5312 0 18.9844 0.203125 19.3594 0.609375C19.7656 1.01563 19.9688 1.48438 19.9688 2.01562V14.0156C19.9688 14.5469 19.7656 15.0156 19.3594 15.4219C18.9844 15.8281 18.5312 16.0312 18 16.0312H1.96875C1.4375 16.0312 0.96875 15.8281 0.5625 15.4219C0.1875 15.0156 0 14.5469 0 14.0156V2.01562C0 1.48438 0.1875 1.01563 0.5625 0.609375C0.96875 0.203125 1.4375 0 1.96875 0H18Z"
                    fill="white" fill-opacity="0.7" />
                </svg>

              </div>

              <div class="flex justify-between items-center w-full">
                <div>
                  <p class="text-sm font-bold text-[#FFFFFFB2] ">Unread Reports</p>
                  <p class="text-sm font-bold text-[#FFFFFF] ">24 Pending</p>
                </div>
                <p class=" rounded-lg text-[10px] text-[#FFFFFF] font-bold px-2 py-1 shadow bg-[#FFFFFF33]  ">Urgent</p>
              </div>

            </div>
          </div>

        </div>

        <div
          class="group relative rounded-xl border border-gray-200/60 bg-white/90 p-4 sm:p-5 shadow-sm backdrop-blur-xl hover:shadow-md transition-all duration-300 ">
          <!-- Animated gradient overlay on hover -->
          <div
            class="absolute inset-0 bg-gradient-to-br from-blue-50/0 via-indigo-50/0 to-purple-50/0 group-hover:from-blue-50/20 group-hover:via-indigo-50/15 group-hover:to-purple-50/20 transition-all duration-500 pointer-events-none">
          </div>

          <div class="flex flex-col sm:flex-row justify-between items-start sm:items-center gap-3 ">
            <h3 class="text-lg font-bold text-gray-900">Recent Activities</h3>
            <div>
              <button class=" text-xs justify-center font-bold text-[#5B13EC] ">
                View All
              </button>
            </div>
          </div>
          <div class="space-y-2 max-h-80 py-3">
            <div v-for="(activity, index) in filteredActivities" :key="index" class="animate-slide-in-right"
              :style="{ animationDelay: `${index * 50}ms` }">
              <ActivityItem :activity="activity" size="sm" variant="minimal" :glow-color="activity.color"
                @click="handleActivityClick" />
            </div>
          </div>
        </div>

        <!-- Compact Upcoming Events -->
        <div
          class="group relative rounded-2xl border border-[#E2E8F0] bg-[#FFFFFF] p-4 sm:p-5 shadow backdrop-blur-xl hover:shadow-md transition-all duration-300 overflow-hidden">
          <!-- Animated gradient overlay on hover -->
          <div
            class="absolute inset-0 bg-gradient-to-br from-orange-50/0 via-amber-50/0 to-yellow-50/0 group-hover:from-orange-50/20 group-hover:via-amber-50/15 group-hover:to-yellow-50/20 transition-all duration-500 pointer-events-none">
          </div>
          <div class="relative z-10">
            <div class="flex justify-between items-start sm:items-center gap-3 mb-4">
              <h3 class="text-lg font-bold text-gray-900">Upcoming Events</h3>
            </div>
            <div class="space-y-2">
              <div v-for="(event, index) in filteredEvents" :key="index" class="animate-slide-in-right"
                :style="{ animationDelay: `${index * 50}ms` }">
                <EventItem :event="event" size="sm" variant="default" @click="handleEventClick" />
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>

    <!-- Compact Notification Toast -->
    <Transition name="slide-fade">
      <div v-if="showNotification"
        class="fixed top-3 right-3 z-50 bg-gradient-to-r from-green-500 to-emerald-600 text-white px-4 py-3 rounded-xl shadow-lg border border-green-200/50 backdrop-blur-sm max-w-xs">
        <div class="flex items-center gap-2">
          <IconCircleCheck :size="16" class="flex-shrink-0" stroke-width="2" />
          <span class="font-semibold text-xs flex-1">{{ notificationMessage }}</span>
          <button @click="showNotification = false"
            class="ml-1 text-white/80 hover:text-white transition-colors p-0.5 hover:bg-white/20 rounded">
            <IconX :size="14" stroke-width="2" />
          </button>
        </div>
      </div>
    </Transition>


    <!-- Compact Quick Actions Floating Button -->
    <div class="fixed bottom-4 right-4 z-40">
      <div class="relative group">
        <button @click="toggleQuickActions"
          class="w-12 h-12 bg-gradient-to-r from-purple-600 via-pink-600 to-rose-600 text-white rounded-xl shadow-lg hover:shadow-xl transition-all duration-200 hover:scale-110 active:scale-95 flex items-center justify-center backdrop-blur-sm border border-white/20">
          <component :is="showQuickActions ? IconX : IconSparkles" :size="20" :stroke-width="2"
            class="transition-transform duration-200" :class="showQuickActions ? 'rotate-90' : ''" />
        </button>

        <Transition name="slide-up">
          <div v-if="showQuickActions"
            class="absolute bottom-16 right-0 bg-white/95 backdrop-blur-xl rounded-xl shadow-xl border border-gray-200/50 p-2 min-w-[180px] space-y-1.5">
            <button @click="quickAction('addStudent')"
              class="w-full flex items-center gap-2 px-3 py-2 rounded-lg hover:bg-blue-50 transition-all duration-200 text-left group">
              <div
                class="w-8 h-8 rounded-lg bg-blue-100 flex items-center justify-center group-hover:bg-blue-200 transition-colors">
                <IconUserPlus :size="14" class="text-blue-600" stroke-width="2" />
              </div>
              <span class="text-gray-900 font-semibold text-xs">Add Student</span>
            </button>
            <button @click="quickAction('addTeacher')"
              class="w-full flex items-center gap-2 px-3 py-2 rounded-lg hover:bg-green-50 transition-all duration-200 text-left group">
              <div
                class="w-8 h-8 rounded-lg bg-green-100 flex items-center justify-center group-hover:bg-green-200 transition-colors">
                <IconSchool :size="14" class="text-green-600" stroke-width="2" />
              </div>
              <span class="text-gray-900 font-semibold text-xs">Add Teacher</span>
            </button>
            <button @click="quickAction('generateReport')"
              class="w-full flex items-center gap-2 px-3 py-2 rounded-lg hover:bg-purple-50 transition-all duration-200 text-left group">
              <div
                class="w-8 h-8 rounded-lg bg-purple-100 flex items-center justify-center group-hover:bg-purple-200 transition-colors">
                <IconFileText :size="14" class="text-purple-600" stroke-width="2" />
              </div>
              <span class="text-gray-900 font-semibold text-xs">Generate Report</span>
            </button>
            <button @click="quickAction('scheduleEvent')"
              class="w-full flex items-center gap-2 px-3 py-2 rounded-lg hover:bg-orange-50 transition-all duration-200 text-left group">
              <div
                class="w-8 h-8 rounded-lg bg-orange-100 flex items-center justify-center group-hover:bg-orange-200 transition-colors">
                <IconCalendarPlus :size="14" class="text-orange-600" stroke-width="2" />
              </div>
              <span class="text-gray-900 font-semibold text-xs">Schedule Event</span>
            </button>
          </div>
        </Transition>
      </div>
    </div>
  </div>
</template>

<style scoped>
/* Modern Transitions */
.slide-fade-enter-active {
  transition: all 0.3s ease-out;
}

.slide-fade-leave-active {
  transition: all 0.2s ease-in;
}

.slide-fade-enter-from {
  transform: translateX(100%);
  opacity: 0;
}

.slide-fade-leave-to {
  transform: translateX(100%);
  opacity: 0;
}

.slide-up-enter-active {
  transition: all 0.3s cubic-bezier(0.34, 1.56, 0.64, 1);
}

.slide-up-leave-active {
  transition: all 0.2s ease-in;
}

.slide-up-enter-from {
  transform: translateY(20px) scale(0.9);
  opacity: 0;
}

.slide-up-leave-to {
  transform: translateY(20px) scale(0.9);
  opacity: 0;
}

/* Icon Bounce Animation */
@keyframes icon-bounce {

  0%,
  100% {
    transform: translateY(0);
  }

  50% {
    transform: translateY(-4px);
  }
}

.animate-icon-bounce {
  animation: icon-bounce 2s ease-in-out infinite;
}

/* Float Animation */
@keyframes float {

  0%,
  100% {
    transform: translateY(0px) translateX(0px);
  }

  50% {
    transform: translateY(-20px) translateX(10px);
  }
}

.animate-float {
  animation: float 6s ease-in-out infinite;
}

.animate-float-delayed {
  animation: float 6s ease-in-out infinite;
  animation-delay: 2s;
}
</style>

<script>
import { ref, onMounted, onBeforeUnmount, computed, nextTick } from 'vue'
import dayjs from 'dayjs'
import axios from 'axios'
import { useStatistics } from '@/composables/useStatistics'
import ActivityItem from '@/components/dashboard/ActivityItem.vue'
import EventItem from '@/components/dashboard/EventItem.vue'
import StatCard from '@/components/dashboard/StatCard.vue'
import ChartJsWrapper from '@/components/charts/ChartJsWrapper.vue'
import HighchartsWrapper from '@/components/charts/HighchartsWrapper.vue'
import CompactDatePicker from '@/components/CompactDatePicker.vue'
import {
  IconWallet,
  IconCircleCheck,
  IconUsers,
  IconUserX,
  IconTrendingUp,
  IconTrendingDown,
  IconClock,
  IconCalendar,
  IconRefresh,
  IconDownload,
  IconCalendarEvent,
  IconUserPlus,
  IconCurrencyDollar,
  IconSchool,
  IconAward,
  IconAlertCircle,
  IconUserCheck,
  IconCreditCard,
  IconBook,
  IconTrophy,
  IconMusic,
  IconSparkles,
  IconChartBar,
  IconChartLine,
  IconLoader2,
  IconX,
  IconFileText,
  IconCalendarPlus,
  IconStars
} from '@tabler/icons-vue'



export default {
  name: 'Dashboard',
  components: {
    StatCard,
    ChartJsWrapper,
    HighchartsWrapper,
    CompactDatePicker,
    ActivityItem,
    EventItem,
    IconWallet,
    IconCircleCheck,
    IconUsers,
    IconUserX,
    IconTrendingUp,
    IconTrendingDown,
    IconClock,
    IconCalendar,
    IconRefresh,
    IconDownload,
    IconCalendarEvent,
    IconUserPlus,
    IconCurrencyDollar,
    IconSchool,
    IconAward,
    IconAlertCircle,
    IconUserCheck,
    IconCreditCard,
    IconBook,
    IconTrophy,
    IconMusic,
    IconSparkles,
    IconChartBar,
    IconChartLine,
    IconLoader2,
    IconX,
    IconFileText,
    IconCalendarPlus,
    IconStars,
    activeFilter: "last30",
  },
  setup() {
    const selectedPeriod = ref('6')
    const feeDistributionPeriod = ref('Monthly')
    const chartView = ref('bar')
    const selectedChartType = ref('bar')
    const selectedPieChartType = ref('pie')
    const chartLoading = ref(false)
    const pieChartLoading = ref(false)
    const refreshing = ref(false)
    const showNotification = ref(false)
    const notificationMessage = ref('')
    const currentTime = ref('')
    const userName = ref('Admin')
    const showQuickActions = ref(false)


    

    // Date filters
    const mainDateFilter = ref({
      startDate: '',
      endDate: '' // For shortcuts (Today, Yesterday, Week, Month)
    })

    const chartDateFilter = ref({
      startDate: ''
    })

  

    const activitiesDateFilter = ref({
      startDate: ''
    })

    const quickStatsDateFilter = ref({
      startDate: ''
    })

    const eventsDateFilter = ref({
      startDate: ''
    })

    // Use statistics composable
    const { statistics, loading: statsLoading, error: statsError } = useStatistics()

    const currentDate = dayjs().format('MMMM D, YYYY')
    const currentHour = dayjs().hour()

    const timeOfDay = computed(() => {
      if (currentHour < 12) return 'morning'
      if (currentHour < 17) return 'afternoon'
      return 'evening'
    })

    const greetingMessage = computed(() => {
      const messages = [
        "Here's what's happening with your school today",
        "Stay updated with real-time insights",
        "Monitor your school's performance at a glance",
        "Track important metrics and trends"
      ]
      return messages[Math.floor(Math.random() * messages.length)]
    })

    // Update time every second
    const updateTime = () => {
      currentTime.value = dayjs().format('HH:mm:ss')
    }

    // Real-time data updates
    const startRealTimeUpdates = () => {
      setInterval(() => {
        // Simulate real-time data updates
        if (Math.random() > 0.7) {
          // Randomly update some statistics
          const randomStat = Math.floor(Math.random() * 4)
          if (randomStat === 0) {
            statisticsCards.value[0].value += Math.floor(Math.random() * 1000)
          } else if (randomStat === 1) {
            statisticsCards.value[1].value += Math.floor(Math.random() * 500)
          }
        }
      }, 30000) // Update every 30 seconds
    }

    // Enhanced activities with Tabler SVG icon components
    // In your component/script setup
    const recentActivities = ref([
      {
        content: 'Fee Payment Received',
        badge: '#1029',
        time: '2 minutes ago',
        type: 'success',
        color: '#10B981',
        colorDark: '#059669',
        details: 'Student: Marcus Wright • $1,250',
        svg: '<svg width="32" height="59" viewBox="0 0 32 59" fill="none" xmlns="http://www.w3.org/2000/svg"><rect width="32" height="32" rx="16" fill="#D1FAE5"/><path d="M14.4883 19.7617L21.2383 13.0117L20.1836 11.9219L14.4883 17.6172L11.8164 14.9453L10.7617 16L14.4883 19.7617ZM10.6914 10.7266C12.168 9.25 13.9375 8.51172 16 8.51172C18.0625 8.51172 19.8203 9.25 21.2734 10.7266C22.75 12.1797 23.4883 13.9375 23.4883 16C23.4883 18.0625 22.75 19.832 21.2734 21.3086C19.8203 22.7617 18.0625 23.4883 16 23.4883C13.9375 23.4883 12.168 22.7617 10.6914 21.3086C9.23828 19.832 8.51172 18.0625 8.51172 16C8.51172 13.9375 9.23828 12.1797 10.6914 10.7266Z" fill="#059669"/><rect width="1" height="19" transform="translate(15.5 36)" fill="#E2E8F0"/></svg>' // checkmark
      },
      {
        content: 'New Student Enrollment',
        time: '45 minutes ago',
        type: 'primary',
        color: '#3B82F6',
        colorDark: '#2563EB',
        details: 'Grade 10 • Sarah Jenkins',
        svg: '<svg width="32" height="59" viewBox="0 0 32 59" fill="none" xmlns="http://www.w3.org/2000/svg"><rect width="32" height="32" rx="16" fill="#DBEAFE"/><path d="M14.2773 18.3555C15.6602 17.793 16.9844 17.5117 18.25 17.5117C19.5156 17.5117 20.8281 17.793 22.1875 18.3555C23.5703 18.8945 24.2617 19.6094 24.2617 20.5V22.0117H12.2383V20.5C12.2383 19.6094 12.918 18.8945 14.2773 18.3555ZM11.5 14.4883H13.75V16H11.5V18.25H9.98828V16H7.73828V14.4883H9.98828V12.2383H11.5V14.4883ZM20.3594 15.1211C19.7734 15.707 19.0703 16 18.25 16C17.4297 16 16.7266 15.707 16.1406 15.1211C15.5547 14.5352 15.2617 13.832 15.2617 13.0117C15.2617 12.1914 15.5547 11.4883 16.1406 10.9023C16.7266 10.293 17.4297 9.98828 18.25 9.98828C19.0703 9.98828 19.7734 10.293 20.3594 10.9023C20.9453 11.4883 21.2383 12.1914 21.2383 13.0117C21.2383 13.832 20.9453 14.5352 20.3594 15.1211Z" fill="#2563EB"/><rect width="1" height="19" transform="translate(15.5 36)" fill="#E2E8F0"/></svg>' // person +
      },
      {
        content: 'Staff Leave Request',
        time: '2 hours ago',
        type: 'warning',
        color: '#F59E0B',
        colorDark: '#D97706',
        badge: 'Pending',
        details: 'Prof. Robert Smith (Medical)',
        svg: '<svg width="32" height="59" viewBox="0 0 32 59" fill="none" xmlns="http://www.w3.org/2000/svg"><rect width="32" height="32" rx="16" fill="#FEF3C7"/><path d="M15.4727 10.5508C15.6133 10.6914 15.7891 10.7617 16 10.7617C16.2109 10.7617 16.3867 10.6914 16.5273 10.5508C16.668 10.3867 16.7383 10.1992 16.7383 9.98828C16.7383 9.77734 16.668 9.60156 16.5273 9.46094C16.3867 9.32031 16.2109 9.25 16 9.25C15.7891 9.25 15.6133 9.32031 15.4727 9.46094C15.332 9.60156 15.2617 9.77734 15.2617 9.98828C15.2617 10.1992 15.332 10.3867 15.4727 10.5508ZM16.7383 17.5117V13.0117H15.2617V17.5117H16.7383ZM16.7383 20.5V18.9883H15.2617V20.5H16.7383ZM21.2383 9.25C21.6367 9.25 21.9883 9.40234 22.293 9.70703C22.5977 10.0117 22.75 10.3633 22.75 10.7617V21.2383C22.75 21.6367 22.5977 21.9883 22.293 22.293C21.9883 22.5977 21.6367 22.75 21.2383 22.75H10.7617C10.3633 22.75 10.0117 22.5977 9.70703 22.293C9.40234 21.9883 9.25 21.6367 9.25 21.2383V10.7617C9.25 10.3633 9.40234 10.0117 9.70703 9.70703C10.0117 9.40234 10.3633 9.25 10.7617 9.25H13.8906C14.0547 8.80469 14.3242 8.44141 14.6992 8.16016C15.0742 7.87891 15.5078 7.73828 16 7.73828C16.4922 7.73828 16.9258 7.87891 17.3008 8.16016C17.6758 8.44141 17.9453 8.80469 18.1094 9.25H21.2383Z" fill="#D97706"/><rect width="1" height="19" transform="translate(15.5 36)" fill="#E2E8F0"/></svg>' // calendar
      },
      {
        content: 'Exam Results Published',
        time: 'Yesterday at 4:30 PM',
        type: 'info',
        color: '#6366F1',
        colorDark: '#4F46E5',
        details: 'Semester 1 • Finals',
        svg: '<svg width="32" height="59" viewBox="0 0 32 59" fill="none" xmlns="http://www.w3.org/2000/svg"><rect width="32" height="32" rx="16" fill="#F3E8FF"/><path d="M16.3867 13.0117V16.1758L18.9883 17.7578L18.4609 18.6719L15.2617 16.7383V13.0117H16.3867ZM22.75 14.5938H17.6523L19.7266 12.4844C18.6953 11.4531 17.4531 10.9375 16 10.9375C14.5703 10.9141 13.3398 11.4062 12.3086 12.4141C11.8867 12.8359 11.5234 13.4102 11.2188 14.1367C10.9141 14.8398 10.7617 15.4844 10.7617 16.0703C10.7617 16.6562 10.9141 17.3125 11.2188 18.0391C11.5234 18.7422 11.8867 19.3047 12.3086 19.7266C12.7305 20.1484 13.3047 20.5117 14.0312 20.8164C14.7578 21.1211 15.4141 21.2734 16 21.2734C16.5859 21.2734 17.2422 21.1211 17.9688 20.8164C18.7188 20.5117 19.3047 20.1484 19.7266 19.7266C20.7344 18.7188 21.2383 17.5 21.2383 16.0703H22.75C22.75 17.9219 22.0938 19.4922 20.7812 20.7812C19.4688 22.0938 17.875 22.75 16 22.75C14.125 22.75 12.5312 22.0938 11.2188 20.7812C9.90625 19.4922 9.25 17.9336 9.25 16.1055C9.25 14.2539 9.90625 12.6719 11.2188 11.3594C11.7578 10.8203 12.4844 10.3633 13.3984 9.98828C14.3359 9.58984 15.1914 9.39062 15.9648 9.39062C16.7383 9.39062 17.582 9.58984 18.4961 9.98828C19.4336 10.3633 20.1719 10.8203 20.7109 11.3594L22.75 9.25V14.5938Z" fill="#9333EA"/></svg>'
      }
    ])

    // Enhanced statistics cards with Tabler SVG icons
    const statisticsCards = ref([
      {
        label: 'Total Fee',
        value: 1850000,
        prefix: 'PKR ',
        suffix: '',
        trend: 'up',
        change: '12% from last month',
        icon: IconWallet,
        iconBg: 'bg-gradient-to-br from-blue-500 via-blue-600 to-indigo-600',
        gradient: 'bg-gradient-to-r from-blue-500 to-indigo-600',
        particleBg: 'bg-blue-400',
        hoverGradient: 'bg-gradient-to-br from-blue-500/10 via-transparent to-indigo-500/10',
        details: 'Total fee collection target for this month'
      },
      {
        label: 'Received Fee',
        value: 1520000,
        prefix: 'PKR ',
        suffix: '',
        trend: 'up',
        change: '8% from last month',
        icon: IconCircleCheck,
        iconBg: 'bg-gradient-to-br from-green-500 via-emerald-600 to-teal-600',
        gradient: 'bg-gradient-to-r from-green-500 to-emerald-600',
        particleBg: 'bg-green-400',
        hoverGradient: 'bg-gradient-to-br from-green-500/10 via-transparent to-emerald-500/10',
        details: 'Successfully collected fees this month'
      },
      {
        label: 'Present Students',
        value: 487,
        prefix: '',
        suffix: '',
        trend: 'up',
        change: '5% from last month',
        icon: IconUsers,
        iconBg: 'bg-gradient-to-br from-amber-500 via-orange-500 to-orange-600',
        gradient: 'bg-gradient-to-r from-amber-500 to-orange-600',
        particleBg: 'bg-amber-400',
        hoverGradient: 'bg-gradient-to-br from-amber-500/10 via-transparent to-orange-500/10',
        details: 'Students present in school today'
      },
      {
        label: 'Absent Students',
        value: 42,
        prefix: '',
        suffix: '',
        trend: 'down',
        change: '3% from last month',
        icon: IconUserX,
        iconBg: 'bg-gradient-to-br from-pink-500 via-rose-500 to-red-600',
        gradient: 'bg-gradient-to-r from-pink-500 to-rose-600',
        particleBg: 'bg-pink-400',
        hoverGradient: 'bg-gradient-to-br from-pink-500/10 via-transparent to-rose-500/10',
        details: 'Students absent today'
      }
    ])

    // Filtered data refs for date filtering
    const filteredActivities = ref([])
    const filteredQuickStats = ref([])
    const filteredEvents = ref([])

    // Quick stats with progress bars and Lucide icons
    const quickStats = ref([
      {
        label: 'New Students',
        value: 24,
        originalValue: 24,
        change: '+12%',
        percentage: 85,
        originalPercentage: 85,
        bgClass: 'from-blue-50 to-indigo-50 border-blue-100',
        textClass: 'text-blue-600',
        valueClass: 'text-blue-800',
        changeClass: 'text-green-600',
        progressClass: 'bg-blue-500',
        iconComponent: IconUserCheck
      },
      {
        label: 'Pending Fees',
        value: 18,
        originalValue: 18,
        change: '-5%',
        percentage: 30,
        originalPercentage: 30,
        bgClass: 'from-rose-50 to-pink-50 border-rose-100',
        textClass: 'text-rose-600',
        valueClass: 'text-rose-800',
        changeClass: 'text-red-600',
        progressClass: 'bg-rose-500',
        iconComponent: IconCreditCard
      },
      {
        label: 'Subjects',
        value: 12,
        originalValue: 12,
        change: '±0%',
        percentage: 100,
        originalPercentage: 100,
        bgClass: 'from-purple-50 to-violet-50 border-purple-100',
        textClass: 'text-purple-600',
        valueClass: 'text-purple-800',
        changeClass: 'text-purple-600',
        progressClass: 'bg-purple-500',
        iconComponent: IconBook
      },
      {
        label: 'Classes',
        value: 8,
        originalValue: 8,
        change: '±0%',
        percentage: 100,
        originalPercentage: 100,
        bgClass: 'from-gray-50 to-slate-50 border-gray-200',
        textClass: 'text-gray-600',
        valueClass: 'text-gray-900',
        changeClass: 'text-gray-600',
        progressClass: 'bg-gray-500',
        iconComponent: IconSchool
      }
    ])

    // Upcoming events with Lucide icons
    const upcomingEvents = ref([
      {
        title: 'Parent-Teacher Meeting',
        month: 'Oct',
        date: '15',
        description: '09:00 AM - 01:00 PM',
        colorClass: 'bg-gradient-to-br from-blue-500 to-indigo-500'
      },
      {
        title: 'Annual Sports Day',
        month: 'Oct',
        date: '25',
        description: 'Main Field • All Day',

        colorClass: 'bg-gradient-to-br from-yellow-500 to-orange-500'
      },
      
    ])

    return {
      selectedPeriod,
      feeDistributionPeriod,
      chartView,
      selectedChartType,
      selectedPieChartType,
      chartLoading,
      pieChartLoading,
      refreshing,
      showNotification,
      notificationMessage,
      currentDate,
      currentTime,
      timeOfDay,
      greetingMessage,
      recentActivities,
      filteredActivities,
      statisticsCards,
      quickStats,
      filteredQuickStats,
      upcomingEvents,
      filteredEvents,
      userName,
      statistics,
      statsLoading,
      statsError,
      updateTime,
      showQuickActions,
      mainDateFilter,
      chartDateFilter,
      pieChartDateFilter,
      activitiesDateFilter,
      quickStatsDateFilter,
      eventsDateFilter
    }
  },
  computed: {
    incomeChartOptions() {
      return {
        responsive: true,
        maintainAspectRatio: false,
        plugins: {
          legend: {
            display: false,
            position: 'top',
            align: 'end',
            labels: {
              // usePointStyle: false,
              padding: 20,
              font: {
                size: 12
              }
            }
          },
          tooltip: {
            backgroundColor: '#1F2937',
            padding: 12,
            titleFont: { size: 14, weight: 'bold' },
            bodyFont: { size: 13 },
            titleColor: '#F9FAFB',
            bodyColor: '#F9FAFB',
            cornerRadius: 8,
            displayColors: true,
            callbacks: {
              label: (context) => `${context.dataset.label}: PKR ${this.formatNumber(context.raw)}`,
              title: (context) => `${context[0].label}`
            }
          }
        },
        scales: {
          y: {
            beginAtZero: true,
            grid: { color: 'rgba(229, 231, 235, 0.5)', drawTicks: false },
            ticks: {
              padding: 10,
              color: '#6B7280',
              callback: value => 'PKR ' + this.formatNumber(value)
            },
            border: { display: false }
          },
          x: {
            grid: { display: false },
            ticks: { color: '#6B7280' },
            border: { display: false }
          }
        },
        animation: { duration: 1500, easing: 'easeOutQuart' },
        layout: { padding: { top: 10, right: 10 } }
      }
    },
    pieChartOptions() {
      const pieData = [
        { name: 'Tuition Fee', y: 55, color: '#3B82F6' },
        { name: 'Examination Fee', y: 20, color: '#10B981' },
        { name: 'Library Fee', y: 10, color: '#F59E0B' },
        { name: 'Transport Fee', y: 10, color: '#6366F1' },
        { name: 'Other Fees', y: 5, color: '#EC4899' }
      ]

      // Determine chart type based on selection
      const chartType = this.selectedPieChartType === 'doughnut' ? 'pie' :
        this.selectedPieChartType === 'column' ? 'column' :
          this.selectedPieChartType === 'bar' ? 'bar' : 'pie'

      return {
        chart: {
          type: chartType,
          backgroundColor: 'transparent',
          animation: {
            duration: 1000,
            easing: 'easeOutQuart'
          }
        },
        title: {
          text: null
        },
        tooltip: {
          pointFormat: '<b>{point.percentage:.1f}%</b><br/>Amount: PKR {point.customAmount}',
          backgroundColor: 'rgba(31, 41, 55, 0.95)',
          style: {
            color: '#F9FAFB'
          }
        },
        plotOptions: {
          pie: {
            allowPointSelect: true,
            cursor: 'pointer',
            innerSize: this.selectedPieChartType === 'doughnut' ? '50%' : '0%',
            dataLabels: {
              enabled: true,
              format: '<b>{point.name}</b>: {point.percentage:.1f} %',
              style: {
                fontSize: '12px',
                fontWeight: '500'
              }
            },
            showInLegend: true,
            animation: {
              duration: 1000
            }
          },
          bar: {
            animation: {
              duration: 1000
            }
          },
          column: {
            animation: {
              duration: 1000
            }
          }
        },
        series: [{
          name: 'Fee Distribution',
          colorByPoint: true,
          data: pieData.map(item => ({
            ...item,
            customAmount: this.formatNumber((item.y / 100) * this.receivedFee)
          }))
        }],
        legend: {
          align: 'center',
          verticalAlign: 'bottom',
          layout: 'horizontal',
          itemStyle: {
            fontSize: '12px',
            fontWeight: '500'
          }
        }
      }
    }
  },
  // data() {
  //   return {
  //     totalFee: 0,
  //     receivedFee: 0,
  //     presentStudents: 0,
  //     absentStudents: 0,
  //     incomeData: {
  //       labels: ['Week 1', 'Week 2', 'Week 3', 'Week 4'],
  //       datasets: [
  //         {
  //           label: 'Current Month',
  //           data: [320000, 380000, 410000, 390000],
  //           backgroundColor: 'rgba(59, 130, 246, 0.8)',
  //           borderColor: '#3B82F6',
  //           borderWidth: 2,
  //           borderRadius: 4,
  //           borderSkipped: false,
  //           tension: 0.4
  //         },
  //         {
  //           label: 'Previous Month',
  //           data: [280000, 350000, 380000, 360000],
  //           backgroundColor: 'rgba(156, 163, 175, 0.8)',
  //           borderColor: '#9CA3AF',
  //           borderWidth: 2,
  //           borderRadius: 4,
  //           borderSkipped: false,
  //           tension: 0.4
  //         }
  //       ]
  //     },
  //     loading: false
  //   }
  //       return {
  //     selectedPeriod: '30',
  //     mainDateFilter: {
  //       startDate: '',
  //       endDate: ''
  //     }
  //   }
  // },

  data() {
    return {
      selectedPeriod: '30',
      showCalendar: false,

      mainDateFilter: {
        startDate: '',
        endDate: ''
      }
    }
  },

  methods: {
    setPeriod(period) {
      this.selectedPeriod = period
      this.showCalendar = false
      this.mainDateFilter.startDate = ''
      this.mainDateFilter.endDate = ''
    },

    methods: {
      buttonClass(period) {
        return [
          'px-4 py-2 text-sm rounded-full transition',
          this.selectedPeriod === period ? 'bg-indigo-600 text-white' : 'text-slate-600 hover:bg-slate-100'
        ];
      }
    },

    toggleCalendar() {
      this.showCalendar = !this.showCalendar
      this.selectedPeriod = ''
    }
  },

  async mounted() {
    // Start time update
    this.updateTime()
    setInterval(this.updateTime, 1000)

    // Start real-time data updates
    this.startRealTimeUpdates()

    // Initialize with sample data first
    this.setSampleData()

    // Initialize filtered data
    this.filteredActivities = [...this.recentActivities]
    this.filteredQuickStats = [...this.quickStats]
    this.filteredEvents = [...this.upcomingEvents]

    await this.$nextTick()
    this.initCharts()
    window.addEventListener('resize', this.handleResize)

    // Then try to fetch real data
    try {
      await this.fetchDashboardData()
    } catch (error) {
      console.error('Error fetching dashboard data:', error)
    }
  },
  beforeUnmount() {
    this.destroyCharts()
    window.removeEventListener('resize', this.handleResize)
  },
  methods: {
    formatNumber(number) {
      // Pakistan number format with commas
      return new Intl.NumberFormat('en-PK', {
        minimumFractionDigits: 0,
        maximumFractionDigits: 0
      }).format(number)
    },

    showNotification(message, duration = 3000) {
      this.notificationMessage = message
      this.showNotification = true
      setTimeout(() => {
        this.showNotification = false
      }, duration)
    },

    async refreshData() {
      this.refreshing = true
      try {
        await this.fetchDashboardData()
        this.showNotification('Data refreshed successfully!')
      } catch (error) {
        this.showNotification('Failed to refresh data. Please try again.', 5000)
      } finally {
        this.refreshing = false
      }
    },

    exportReport() {
      this.showNotification('Exporting report...')
      // Implement export functionality
    },

    showStatDetails(payload) {
      const stat = payload?.data || payload || payload?.stat
      if (stat) {
        this.showNotification(`Viewing details for ${stat.label}`)
        // Implement modal or navigation to detailed view
      }
    },

    showActivityDetails(activity) {
      this.showNotification(`Viewing activity: ${activity.content}`)
      // Implement modal with activity details
    },

    handleActivityClick(payload) {
      const activity = payload.data || payload
      this.showActivityDetails(activity)
    },

    handleEventClick(payload) {
      const event = payload.data || payload
      this.showNotification(`Viewing event: ${event.title}`)
      // Implement modal with event details
    },

    showQuickStatDetails(stat) {
      this.showNotification(`Viewing details for ${stat.label}`)
      // Implement detailed view
    },

    viewAllActivities() {
      this.showNotification('Opening all activities...')
      // Navigate to activities page
    },

    viewAllStats() {
      this.showNotification('Opening all stats...')
      // Navigate to stats page
    },

    toggleChartView() {
      this.chartView = this.chartView === 'bar' ? 'line' : 'bar'
      this.updateChartData()
    },

    handleChartTypeChange() {
      // Update chart view based on selected chart type
      this.chartView = this.selectedChartType
      this.updateChartData()
    },

    handlePieChartTypeChange() {
      // Update pie chart type (this will be handled by HighchartsWrapper)
      this.updatePieChartData()
    },

    updateChartData() {
      this.chartLoading = true
      setTimeout(() => {
        this.chartLoading = false
        if (this.incomeChart) {
          this.incomeChart.update()
        }
      }, 1000)
    },

    updatePieChart() {
      this.pieChartLoading = true
      setTimeout(() => {
        this.pieChartLoading = false
        if (this.pieChart) {
          this.pieChart.update()
        }
      }, 1000)
    },

    getStatusClass(type) {
      const classes = {
        success: 'bg-green-100 text-green-800',
        primary: 'bg-blue-100 text-blue-800',
        warning: 'bg-yellow-100 text-yellow-800',
        info: 'bg-indigo-100 text-indigo-800'
      }
      return classes[type] || classes.info
    },

    toggleQuickActions() {
      this.showQuickActions = !this.showQuickActions
    },

    quickAction(action) {
      this.showQuickActions = false

      switch (action) {
        case 'addStudent':
          this.showNotification('Opening student registration form...')
          // Navigate to student registration
          this.$router.push('/students/registration')
          break
        case 'addTeacher':
          this.showNotification('Opening teacher registration form...')
          // Navigate to teacher registration
          this.$router.push('/faculty/add-teacher')
          break
        case 'generateReport':
          this.showNotification('Generating comprehensive report...')
          // Implement report generation
          break
        case 'scheduleEvent':
          this.showNotification('Opening event scheduler...')
          // Navigate to event management
          this.$router.push('/events/create')
          break
        default:
          this.showNotification('Action not implemented yet')
      }
    },

    startRealTimeUpdates() {
      setInterval(() => {
        // Simulate real-time data updates
        if (Math.random() > 0.7) {
          // Randomly update some statistics
          const randomStat = Math.floor(Math.random() * 4)
          if (randomStat === 0) {
            this.statisticsCards[0].value += Math.floor(Math.random() * 1000)
          } else if (randomStat === 1) {
            this.statisticsCards[1].value += Math.floor(Math.random() * 500)
          }
        }
      }, 30000) // Update every 30 seconds
    },

    // Date filter methods
    // Date filter methods - Each section has independent date filter
    handleMainDateChange(value) {
      this.setDateFilter(this.mainDateFilter, value)
      this.updateActivitiesData()
      this.updateEventsData()
    },

    handleChartDateChange(value) {
      this.setDateFilter(this.chartDateFilter, value)
      this.updateChartData()
    },

    handlePieChartDateChange(value) {
      this.setDateFilter(this.pieChartDateFilter, value)
      this.updatePieChartData()
    },

    handleQuickStatsDateChange(value) {
      this.setDateFilter(this.quickStatsDateFilter, value)
      this.updateQuickStatsData()
    },

    setDateFilter(filter, value) {
      // If value is array (range from shortcuts like Today, Yesterday, Week, Month)
      if (Array.isArray(value) && value.length === 2) {
        // Store as array so CompactDatePicker can show both dates
        filter.startDate = value // Store array [startDate, endDate]
        filter.endDate = value[1]   // Keep endDate for backward compatibility
      } else {
        // Single date selected - always set start date and end date to same date with times
        if (value) {
          // Remove time if present, get only date part
          let dateStr = value
          if (value.includes(' ')) {
            dateStr = value.split(' ')[0]
          } else if (value.includes('T')) {
            dateStr = value.split('T')[0]
          }

          // Set as array format so CompactDatePicker shows both dates
          const startDateStr = `${dateStr} 00:00:00`
          const endDateStr = `${dateStr} 23:59:59`
          filter.startDate = [startDateStr, endDateStr] // Store as array
          filter.endDate = endDateStr // Keep for backward compatibility
        } else {
          filter.startDate = null
          filter.endDate = ''
        }
      }
    },

    applyMainDateFilter() {
      // Apply main date filter to all sections (optional - can be removed if not needed)
      this.updateChartData()
      this.updatePieChartData()
      this.updateActivitiesData()
      this.updateQuickStatsData()
      this.updateEventsData()

      this.showNotification('Main date filter applied to all sections')
    },

    clearMainDateFilter() {
      this.mainDateFilter.startDate = ''
      this.mainDateFilter.endDate = ''

      // Update all data (all sections use mainDateFilter now)
      this.updateChartData()
      this.updatePieChartData()
      this.updateActivitiesData()
      this.updateQuickStatsData()
      this.updateEventsData()

      this.showNotification('All date filters cleared')
    },

    updateChartData() {
      // Update chart data based on date filter
      this.chartLoading = true
      setTimeout(() => {
        this.chartLoading = false
        if (this.chart) {
          this.chart.update()
        }
      }, 1000)
    },

    updatePieChartData() {
      // Update pie chart data based on pie chart date filter
      if (this.pieChartDateFilter.startDate) {
        let startDate, endDate

        // Handle array format (from shortcuts or single date)
        if (Array.isArray(this.pieChartDateFilter.startDate)) {
          startDate = new Date(this.pieChartDateFilter.startDate[0]?.split(' ')[0] || this.pieChartDateFilter.startDate[0])
          endDate = new Date(this.pieChartDateFilter.startDate[1]?.split(' ')[0] || this.pieChartDateFilter.startDate[1] || this.pieChartDateFilter.endDate?.split(' ')[0])
        } else {
          startDate = new Date(this.pieChartDateFilter.startDate?.split(' ')[0] || this.pieChartDateFilter.startDate)
          endDate = new Date(this.pieChartDateFilter.endDate?.split(' ')[0] || this.pieChartDateFilter.endDate || this.pieChartDateFilter.startDate)
        }

        // Use dates for filtering if needed
      }

      this.pieChartLoading = true
      setTimeout(() => {
        this.pieChartLoading = false
        if (this.pieChart) {
          this.pieChart.update()
        }
      }, 1000)
    },

    updateActivitiesData() {
      // Filter activities based on main date filter (activities use main filter)
      if (this.mainDateFilter.startDate) {
        let startDate, endDate

        // Handle array format (from shortcuts or single date)
        if (Array.isArray(this.mainDateFilter.startDate)) {
          startDate = new Date(this.mainDateFilter.startDate[0]?.split(' ')[0] || this.mainDateFilter.startDate[0])
          endDate = new Date(this.mainDateFilter.startDate[1]?.split(' ')[0] || this.mainDateFilter.startDate[1] || this.mainDateFilter.endDate?.split(' ')[0])
        } else {
          startDate = new Date(this.mainDateFilter.startDate?.split(' ')[0] || this.mainDateFilter.startDate)
          endDate = new Date(this.mainDateFilter.endDate?.split(' ')[0] || this.mainDateFilter.endDate || this.mainDateFilter.startDate)
        }

        // Filter activities based on their time (simulating date-based filtering)
        this.filteredActivities = this.recentActivities.filter((activity, index) => {
          // Simulate date-based filtering by using index as days ago
          const activityDate = new Date()
          activityDate.setDate(activityDate.getDate() - (index + 1))
          return activityDate >= startDate && activityDate <= endDate
        })

        this.showNotification('Activities filtered for selected date range')
      } else {
        this.filteredActivities = this.recentActivities
      }
    },

    updateQuickStatsData() {
      // Filter quick stats based on quick stats date filter
      if (this.quickStatsDateFilter.startDate) {
        let startDate, endDate

        // Handle array format (from shortcuts or single date)
        if (Array.isArray(this.quickStatsDateFilter.startDate)) {
          startDate = new Date(this.quickStatsDateFilter.startDate[0]?.split(' ')[0] || this.quickStatsDateFilter.startDate[0])
          endDate = new Date(this.quickStatsDateFilter.startDate[1]?.split(' ')[0] || this.quickStatsDateFilter.startDate[1] || this.quickStatsDateFilter.endDate?.split(' ')[0])
        } else {
          startDate = new Date(this.quickStatsDateFilter.startDate?.split(' ')[0] || this.quickStatsDateFilter.startDate)
          endDate = new Date(this.quickStatsDateFilter.endDate?.split(' ')[0] || this.quickStatsDateFilter.endDate || this.quickStatsDateFilter.startDate)
        }

        // Simulate filtering by adjusting values based on date
        this.filteredQuickStats = this.quickStats.map(stat => {
          const daysDiff = Math.floor((endDate - startDate) / (1000 * 60 * 60 * 24))
          const multiplier = Math.max(0.5, Math.min(1.5, daysDiff / 30)) // Adjust based on date range

          return {
            ...stat,
            value: Math.floor(stat.originalValue * multiplier),
            percentage: Math.min(100, Math.floor(stat.originalPercentage * multiplier))
          }
        })

        this.showNotification('Quick stats filtered for selected date range')
      } else {
        this.filteredQuickStats = this.quickStats
      }
    },

    updateEventsData() {
      // Filter events based on main date filter (events use main filter)
      if (this.mainDateFilter.startDate) {
        let startDate, endDate

        // Handle array format (from shortcuts or single date)
        if (Array.isArray(this.mainDateFilter.startDate)) {
          startDate = new Date(this.mainDateFilter.startDate[0]?.split(' ')[0] || this.mainDateFilter.startDate[0])
          endDate = new Date(this.mainDateFilter.startDate[1]?.split(' ')[0] || this.mainDateFilter.startDate[1] || this.mainDateFilter.endDate?.split(' ')[0])
        } else {
          startDate = new Date(this.mainDateFilter.startDate?.split(' ')[0] || this.mainDateFilter.startDate)
          endDate = new Date(this.mainDateFilter.endDate?.split(' ')[0] || this.mainDateFilter.endDate || this.mainDateFilter.startDate)
        }

        // Filter events based on their date
        this.filteredEvents = this.upcomingEvents.filter(event => {
          const eventDate = new Date(event.date)
          return eventDate >= startDate && eventDate <= endDate
        })

        this.showNotification('Events filtered for selected date range')
      } else {
        this.filteredEvents = this.upcomingEvents
      }
    },

    setSampleData() {
      // Sample data for income chart
      this.incomeData = {
        labels: ['Week 1', 'Week 2', 'Week 3', 'Week 4'],
        datasets: [
          {
            label: '',
            data: [320000, 380000, 410000, 390000],
            backgroundColor: 'rgba(59, 130, 246, 0.8)',
            borderColor: '#3B82F6',
            borderWidth: 2,
            borderRadius: 4,
            borderSkipped: false,
            tension: 0.4,
            pointRadius: 0 // <-- removes dots
          },
          {
            label: '',
            data: [280000, 350000, 380000, 360000],
            backgroundColor: 'rgba(156, 163, 175, 0.8)',
            borderColor: '#9CA3AF',
            borderWidth: 2,
            borderRadius: 4,
            borderSkipped: false,
            tension: 0.4,
            pointRadius: 0 // <-- removes dots
          }
        ]
      };


      // Sample data for pie chart
      this.pieData = {
        labels: ['Tuition Fee', 'Examination Fee', 'Library Fee', 'Transport Fee', 'Other Fees'],
        datasets: [{
          data: [55, 20, 10, 10, 5],
          backgroundColor: [
            '#3B82F6',
            '#10B981',
            '#F59E0B',
            '#6366F1',
            '#EC4899'
          ],
          borderWidth: 0
        }]
      }

      // Sample statistics
      this.totalFee = 1850000
      this.receivedFee = 1520000
      this.presentStudents = 487
      this.absentStudents = 42
    },

    initCharts() {
      // Charts are now handled by ChartJsWrapper and HighchartsWrapper components
      // No manual initialization needed
    },

    async fetchDashboardData() {
      try {
        this.loading = true

        // Fetch monthly income data
        const incomeResponse = await axios.get('/api/admin/dashboard/monthly-income', {
          params: {
            period: this.selectedPeriod
          }
        })

        // Fetch fee distribution data
        const distributionResponse = await axios.get('/api/admin/dashboard/fee-distribution', {
          params: {
            period: this.feeDistributionPeriod
          }
        })

        // Update income chart data
        this.incomeData.labels = incomeResponse.data.data.labels
        this.incomeData.datasets[0].data = incomeResponse.data.data.currentMonth
        this.incomeData.datasets[1].data = incomeResponse.data.data.previousMonth

        // Update pie chart data
        this.pieData.labels = distributionResponse.data.data.labels
        this.pieData.datasets[0].data = distributionResponse.data.data.values

        // Update statistics
        this.totalFee = incomeResponse.data.data.totalFee
        this.receivedFee = incomeResponse.data.data.receivedFee
        this.presentStudents = incomeResponse.data.data.presentStudents
        this.absentStudents = incomeResponse.data.data.absentStudents

        // Update charts with new data
        if (this.$refs.incomeChart) {
          this.$refs.incomeChart.update()
        }
        if (this.$refs.pieChart) {
          this.$refs.pieChart.update()
        }
      } catch (error) {
        console.error('Error fetching dashboard data:', error)
        // Fallback to sample data if API fails
        this.setSampleData()
      } finally {
        this.loading = false
      }
    },

    destroyCharts() {
      // Charts are now handled by ChartJsWrapper and HighchartsWrapper components
      // They will auto-destroy on component unmount
    },

    handleResize() {
      this.destroyCharts()
      this.initCharts()
    }
  },
  watch: {
    selectedPeriod() {
      this.fetchDashboardData()
    },
    feeDistributionPeriod() {
      this.fetchDashboardData()
    }
  }
}
</script>

<style scoped>
/* Import modern fonts */
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@100;200;300;400;500;600;700;800;900&display=swap');

/* Modern Icon Animations */
@keyframes icon-bounce {

  0%,
  100% {
    transform: translateY(0) scale(1);
  }

  50% {
    transform: translateY(-3px) scale(1.05);
  }
}

@keyframes float {

  0%,
  100% {
    transform: translateY(0) translateX(0);
  }

  33% {
    transform: translateY(-10px) translateX(5px);
  }

  66% {
    transform: translateY(-5px) translateX(-5px);
  }
}

@keyframes float-delayed {

  0%,
  100% {
    transform: translateY(0) translateX(0);
  }

  33% {
    transform: translateY(-8px) translateX(-4px);
  }

  66% {
    transform: translateY(-4px) translateX(6px);
  }
}

@keyframes bounce-slow {

  0%,
  100% {
    transform: translateY(0);
  }

  50% {
    transform: translateY(-4px);
  }
}

@keyframes pulse-ring {
  0% {
    transform: scale(0.95);
    opacity: 0.5;
  }

  50% {
    transform: scale(1.05);
    opacity: 0.3;
  }

  100% {
    transform: scale(0.95);
    opacity: 0.5;
  }
}

@keyframes fade-in-up {
  from {
    opacity: 0;
    transform: translateY(10px);
  }

  to {
    opacity: 1;
    transform: translateY(0);
  }
}

@keyframes slide-in-right {
  from {
    opacity: 0;
    transform: translateX(-10px);
  }

  to {
    opacity: 1;
    transform: translateX(0);
  }
}

@keyframes scale-in {
  from {
    opacity: 0;
    transform: scale(0.95);
  }

  to {
    opacity: 1;
    transform: scale(1);
  }
}

.animate-icon-bounce {
  animation: icon-bounce 2s ease-in-out infinite;
}

.animate-float {
  animation: float 6s ease-in-out infinite;
}

.animate-float-delayed {
  animation: float-delayed 7s ease-in-out infinite;
  animation-delay: 1s;
}

.animate-bounce-slow {
  animation: bounce-slow 2s ease-in-out infinite;
}

.animate-fade-in-up {
  animation: fade-in-up 0.6s ease-out forwards;
  opacity: 0;
}

.animate-slide-in-right {
  animation: slide-in-right 0.5s ease-out forwards;
  opacity: 0;
}

.animate-scale-in {
  animation: scale-in 0.4s ease-out forwards;
  opacity: 0;
}

.animate-fade-in-up {
  animation: fade-in-up 0.6s ease-out forwards;
  opacity: 0;
}

.animate-slide-in-right {
  animation: slide-in-right 0.5s ease-out forwards;
  opacity: 0;
}

.animate-scale-in {
  animation: scale-in 0.4s ease-out forwards;
  opacity: 0;
}

/* Chart container adjustments for better responsive behavior */
.h-80 canvas {
  width: 100% !important;
  height: 100% !important;
}

/* Custom scrollbar for activities */
.max-h-96::-webkit-scrollbar {
  width: 6px;
}

.max-h-96::-webkit-scrollbar-track {
  background: transparent;
}

.max-h-96::-webkit-scrollbar-thumb {
  background: linear-gradient(135deg, #c084fc, #a855f7);
  border-radius: 8px;
  min-height: 40px;
}

.max-h-96::-webkit-scrollbar-thumb:hover {
  background: linear-gradient(135deg, #a855f7, #9333ea);
}

/* Enhanced hover effects */
.group:hover .w-14 {
  transform: scale(1.1);
  transition: transform 0.2s ease;
}

/* Animation for containers */
@keyframes fadeInUp {
  from {
    opacity: 0;
    transform: translateY(20px);
  }

  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.rounded-2xl {
  animation: fadeInUp 0.6s ease-out;
}

/* Staggered animation for stats cards */
.grid>div:nth-child(1) {
  animation-delay: 0.1s;
}

.grid>div:nth-child(2) {
  animation-delay: 0.2s;
}

.grid>div:nth-child(3) {
  animation-delay: 0.3s;
}

.grid>div:nth-child(4) {
  animation-delay: 0.4s;
}

/* Gradient text effect */
.text-purple-600 {
  background: linear-gradient(135deg, #7c3aed, #a855f7);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

/* Enhanced backdrop blur for glass morphism */
.backdrop-filter {
  backdrop-filter: blur(20px);
  -webkit-backdrop-filter: blur(20px);
}

/* Better button hover effects */
button:hover {
  transform: translateY(-1px);
  transition: all 0.2s ease;
}

/* Enhanced typography */
h1,
h2,
h3,
h4,
h5,
h6 {
  font-family: 'Poppins', system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
  font-feature-settings: 'cv02', 'cv03', 'cv04', 'cv11';
}

.font-black {
  font-weight: 900;
  letter-spacing: -0.025em;
}

.font-extrabold {
  font-weight: 800;
  letter-spacing: -0.025em;
}

.tracking-tight {
  letter-spacing: -0.025em;
}

.tracking-wide {
  letter-spacing: 0.025em;
}

/* Chart responsiveness */
@media (max-width: 640px) {
  .h-80 {
    height: 240px;
  }

  .text-4xl {
    font-size: 2.5rem;
  }

  .text-3xl {
    font-size: 2rem;
  }

  .text-2xl {
    font-size: 1.75rem;
  }
}

@media (max-width: 1024px) {
  .lg\:col-span-2 {
    grid-column: span 1 !important;
  }
}

/* Enhanced accessibility and focus states */
button:focus-visible {
  outline: 2px solid #7c3aed;
  outline-offset: 2px;
}

select:focus-visible {
  outline: 2px solid #7c3aed;
  outline-offset: 2px;
}

/* Smooth transitions for all interactive elements */
* {
  transition-property: color, background-color, border-color, text-decoration-color, fill, stroke, opacity, box-shadow, transform, filter, backdrop-filter;
  transition-timing-function: cubic-bezier(0.4, 0, 0.2, 1);
  transition-duration: 150ms;
}

/* Notification animation */
@keyframes slideIn {
  from {
    transform: translateX(100%);
    opacity: 0;
  }

  to {
    transform: translateX(0);
    opacity: 1;
  }
}

/* Pulse animation for online indicator */
@keyframes pulse {

  0%,
  100% {
    opacity: 1;
  }

  50% {
    opacity: 0.5;
  }
}

.animate-pulse {
  animation: pulse 2s cubic-bezier(0.4, 0, 0.6, 1) infinite;
}

/* Enhanced glass morphism */
.glass-effect {
  background: rgba(255, 255, 255, 0.25);
  backdrop-filter: blur(10px);
  border: 1px solid rgba(255, 255, 255, 0.18);
}

/* Loading spinner */
@keyframes spin {
  to {
    transform: rotate(360deg);
  }
}

.fa-spin {
  animation: spin 1s linear infinite;
}

/* Floating button animations */
@keyframes float {

  0%,
  100% {
    transform: translateY(0px);
  }

  50% {
    transform: translateY(-10px);
  }
}

.floating-button {
  animation: float 3s ease-in-out infinite;
}

/* Enhanced shadow for floating button */
.shadow-3xl {
  box-shadow: 0 25px 50px -12px rgba(0, 0, 0, 0.25);
}

/* Quick actions menu animation */
.quick-actions-enter-active,
.quick-actions-leave-active {
  transition: all 0.3s ease;
}

.quick-actions-enter-from,
.quick-actions-leave-to {
  opacity: 0;
  transform: translateY(10px) scale(0.95);
}

/* Enhanced notification animation */
@keyframes slideInRight {
  from {
    transform: translateX(100%);
    opacity: 0;
  }

  to {
    transform: translateX(0);
    opacity: 1;
  }
}

.notification-enter-active {
  animation: slideInRight 0.3s ease-out;
}

.notification-leave-active {
  animation: slideInRight 0.3s ease-out reverse;
}
</style>

<style>
.custom-select-dropdown {
  border-radius: 8px !important;
  box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1), 0 2px 4px -1px rgba(0, 0, 0, 0.06) !important;
  border: none !important;
}

.custom-select-dropdown .el-select-dropdown__item {
  padding: 8px 16px !important;
  font-size: 13px !important;
}

.custom-select-dropdown .el-select-dropdown__item.hover {
  background-color: #EFF6FF !important;
}

.custom-timeline .el-timeline-item__tail {
  border-left: 2px dashed #E5E7EB !important;
}

.custom-timeline .el-timeline-item__node {
  width: 12px !important;
  height: 12px !important;
  left: -5px !important;
}

.custom-timeline .el-timeline-item__timestamp {
  color: #9CA3AF !important;
  font-size: 12px !important;
  margin-top: 4px !important;
}


@keyframes slide-in-right {
  from {
    opacity: 0;
    transform: translateX(20px);
  }

  to {
    opacity: 1;
    transform: translateX(0);
  }
}

.animate-slide-in-right {
  animation: slide-in-right 0.5s ease-out forwards;
}
</style>
