<template>
  <div class="fee-collection-ultra">
    <!-- Modern Soft Fee Summary Section -->
    <!-- <div class="modern-fee-summary-grid">
      <div class="modern-fee-summary-card modern-blue">
        <div style="display: flex; align-items: center; gap: 18px;">
          <span style="font-size: 2.2rem; background: rgba(255,255,255,0.13); border-radius: 50%; padding: 12px; display: flex; align-items: center; justify-content: center;">
            <svg width="32" height="32" fill="none" viewBox="0 0 24 24"><rect width="32" height="32" rx="16" fill="#2563eb"/><path d="M12 7v10M7 12h10" stroke="#fff" stroke-width="2.2" stroke-linecap="round"/></svg>
          </span>
          <div>
            <div class="modern-fee-summary-label">Received Fee</div>
            <div class="modern-fee-summary-value">₹15,20,000</div>
            <div style="color: #10b981; font-weight: 600; font-size: 1rem; margin-top: 2px;">↑ 2% this month</div>
          </div>
        </div>
      </div>
      <div class="modern-fee-summary-card modern-purple">
        <div style="display: flex; align-items: center; gap: 18px;">
          <span style="font-size: 2.2rem; background: rgba(255,255,255,0.13); border-radius: 50%; padding: 12px; display: flex; align-items: center; justify-content: center;">
            <svg width="32" height="32" fill="none" viewBox="0 0 24 24"><rect width="32" height="32" rx="16" fill="#a21caf"/><path d="M12 7v10M7 12h10" stroke="#fff" stroke-width="2.2" stroke-linecap="round"/></svg>
          </span>
          <div>
            <div class="modern-fee-summary-label">Remaining Fee</div>
            <div class="modern-fee-summary-value">₹3,30,000</div>
            <div style="color: #ef4444; font-weight: 600; font-size: 1rem; margin-top: 2px;">↓ 1% this month</div>
          </div>
        </div>
      </div>
      <div class="modern-fee-summary-card modern-blue" style="background: linear-gradient(135deg, rgba(16,185,129,0.96) 70%, rgba(110,231,183,0.90) 100%);">
        <div style="display: flex; align-items: center; gap: 18px;">
          <span style="font-size: 2.2rem; background: rgba(255,255,255,0.13); border-radius: 50%; padding: 12px; display: flex; align-items: center; justify-content: center;">
            <svg width="32" height="32" fill="none" viewBox="0 0 24 24"><rect width="32" height="32" rx="16" fill="#10b981"/><path d="M12 7v10M7 12h10" stroke="#fff" stroke-width="2.2" stroke-linecap="round"/></svg>
          </span>
          <div>
            <div class="modern-fee-summary-label">Monthly Fee</div>
            <div class="modern-fee-summary-value">₹1,50,000</div>
            <div style="color: #10b981; font-weight: 600; font-size: 1rem; margin-top: 2px;">↑ 3% this month</div>
          </div>
        </div>
      </div>
      <div class="modern-fee-summary-card modern-yellow">
        <div style="display: flex; align-items: center; gap: 18px;">
          <span style="font-size: 2.2rem; background: rgba(255,255,255,0.13); border-radius: 50%; padding: 12px; display: flex; align-items: center; justify-content: center;">
            <svg width="32" height="32" fill="none" viewBox="0 0 24 24"><rect width="32" height="32" rx="16" fill="#fbbf24"/><path d="M12 7v10M7 12h10" stroke="#fff" stroke-width="2.2" stroke-linecap="round"/></svg>
          </span>
          <div>
            <div class="modern-fee-summary-label">Yearly Fee</div>
            <div class="modern-fee-summary-value">₹18,00,000</div>
            <div style="color: #10b981; font-weight: 600; font-size: 1rem; margin-top: 2px;">↑ 5% this year</div>
          </div>
        </div>
      </div>
      <div class="modern-fee-summary-card modern-yellow" style="background: linear-gradient(135deg, rgba(251,191,36,0.96) 70%, rgba(253,230,138,0.90) 100%);">
        <div style="display: flex; align-items: center; gap: 18px;">
          <span style="font-size: 2.2rem; background: rgba(255,255,255,0.13); border-radius: 50%; padding: 12px; display: flex; align-items: center; justify-content: center;">
            <svg width="32" height="32" fill="none" viewBox="0 0 24 24"><rect width="32" height="32" rx="16" fill="#fbbf24"/><path d="M12 7v10M7 12h10" stroke="#fff" stroke-width="2.2" stroke-linecap="round"/></svg>
          </span>
          <div>
            <div class="modern-fee-summary-label">Total Fee (All Time)</div>
            <div class="modern-fee-summary-value">₹25,00,000</div>
          </div>
        </div>
      </div>
    </div> -->
    <!-- Earnings/Expenses Chart -->
    <!-- <div class="chart-card glass-blur">
      <div class="chart-header">
        <div class="chart-title">Earnings</div>
        <div class="chart-dropdown-wrap">
          <select v-model="selectedMonths" class="chart-dropdown">
            <option v-for="opt in monthsOptions" :key="opt" :value="opt">{{ opt }}</option>
          </select>
          <span class="chevron">▼</span>
        </div>
      </div>
      <VueApexCharts width="100%" height="260" type="area" :options="chartOptions" :series="series" />
    </div> -->

    <!-- Main Fee Sections -->
    <div class="fee-sections-container">
      <div class="section-header flex justify-between ">
        <!-- <h2 class="section-title">Fee Management Modules</h2>
        <p class="section-subtitle">Access the core modules of the fee system</p> -->
        <div class="flex flex-col ">
          <h2 class="section-title">Fee Management Hub</h2>
          <p class="section-subtitle">Manage, generate, and track all institutional financial records.</p>
        </div>
        <div class="align-bottom pt-4">
          <button
            class="flex gap-2 bg-[#FFFFFF] border border-[#E2E8F0] shadow-transparent rounded-[16px] px-3 py-2.5 justify-center items-center text-[#0F172A] font-inter font-bold leading-5 tracking-[0%]  text-sm">
            <svg width="11" height="13" viewBox="0 0 11 13" fill="none" xmlns="http://www.w3.org/2000/svg">
              <path
                d="M0 12.7617V11.25H10.4766V12.7617H0ZM10.4766 4.5L5.23828 9.73828L0 4.5H2.98828V0H7.48828V4.5H10.4766Z"
                fill="#0F172A" />
            </svg>
            Export PDF
          </button>
        </div>

      </div>

      <div class="flex justify-between ">
        <div class=" bg-white flex flex-col rounded-3xl w-[352px] h-[132px]  p-4 cursor-pointer">
          <!-- Header -->
          <div class="flex justify-between  ">
            <p class="text-sm text-[#64748B] font-medium tracking-[0%] ">
              Total Revenue
            </p>

            <span
              class="flex items-center gap-1 text-sm font-semibold text-green-600 bg-green-100 px-2 py-1 rounded-lg">
              <svg width="10" height="6" viewBox="0 0 10 6" fill="none" xmlns="http://www.w3.org/2000/svg">
                <path
                  d="M6.98438 0H9.98438V3L8.83594 1.85156L5.69531 4.99219L3.70312 3L0.703125 6L0 5.29688L3.70312 1.59375L5.69531 3.58594L8.13281 1.14844L6.98438 0Z"
                  fill="#047857" />
              </svg>

              +12%
            </span>
          </div>

          <!-- Amount -->
          <h2 class=" text-3xl font-bold text-[#0F172A]">
            $450,000
          </h2>

          <!-- Progress Bar -->
          <div class="mt-2 h-2 w-full bg-[#F1F5F9] rounded-full overflow-hidden">
            <div class="h-full w-[70%] bg-[#5B13EC] rounded-full"></div>
          </div>
        </div>

        <div class=" bg-white flex flex-col rounded-3xl w-[352px] h-[132px]  p-4 cursor-pointer">
          <!-- Header -->
          <div class="flex justify-between items-center">
            <p class="text-sm text-[#64748B] font-medium">
              Outstanding Fees
            </p>

            <span
              class="flex items-center gap-1 text-sm font-semibold text-[#BE123C] bg-[#FFE4E6] px-2 py-1 rounded-lg">
              <svg width="10" height="6" viewBox="0 0 10 6" fill="none" xmlns="http://www.w3.org/2000/svg">
                <path
                  d="M6.98438 6L8.13281 4.85156L5.69531 2.41406L3.70312 4.40625L0 0.703125L0.703125 0L3.70312 3L5.69531 1.00781L8.83594 4.14844L9.98438 3V6H6.98438Z"
                  fill="#BE123C" />
              </svg>

              -5%
            </span>
          </div>

          <!-- Amount -->
          <h2 class=" text-3xl font-bold text-[#0F172A]">
            $450,000
          </h2>

          <!-- Progress Bar -->
          <div class="mt-2  h-2 w-full bg-[#F1F5F9] rounded-full overflow-hidden">
            <div class="h-full w-[70%] bg-[#F59E0B] rounded-full"></div>
          </div>
        </div>

        <div class=" bg-white flex flex-col rounded-3xl w-[352px] h-[132px]  p-4 cursor-pointer">
          <!-- Header -->
          <div class="flex justify-between items-center">
            <p class="text-sm text-[#64748B] font-medium">
              Collection Rate
            </p>

            <span
              class="flex items-center gap-1 text-sm font-semibold text-[#5B13EC] bg-[#5B13EC1A] px-2 py-1 rounded-lg">
              <svg width="9" height="9" viewBox="0 0 9 9" fill="none" xmlns="http://www.w3.org/2000/svg">
                <path
                  d="M6 2.50781H8.01562V8.01562H6V2.50781ZM0 8.01562V4.00781H2.01562V8.01562H0ZM3 8.01562V0H5.01562V8.01562H3Z"
                  fill="#5B13EC" />
              </svg>

              +12%
            </span>
          </div>

          <!-- Amount -->
          <h2 class=" text-3xl font-bold text-[#0F172A]">
            $450,000
          </h2>

          <!-- Progress Bar -->
          <div class="mt-2 h-2 w-full bg-[#F1F5F9] rounded-full overflow-hidden">
            <div class="h-full w-[70%] bg-[#10B981] rounded-full"></div>
          </div>
        </div>

      </div>


      <div class="fee-sections-grid">
        <!-- Generate Fee Module -->
        <!-- <div class="fee-section-card glass flex flex-col justify-normal" @click="goToGenerateChallan">
          <div class="flex justify-between items-center ">
            <div class="section-icon structure-icon justify-start items-start">
              <svg width="56" height="56" viewBox="0 0 56 56" fill="none" xmlns="http://www.w3.org/2000/svg">
                <rect width="56" height="56" rx="24" fill="#5B13EC" />
                <path
                  d="M34.2695 29.2305V26.7695H29.2305V21.7305H26.7695V26.7695H21.7305V29.2305H26.7695V34.2695H29.2305V29.2305H34.2695ZM19.1523 19.2109C21.6133 16.75 24.5625 15.5195 28 15.5195C31.4375 15.5195 34.3672 16.75 36.7891 19.2109C39.25 21.6328 40.4805 24.5625 40.4805 28C40.4805 31.4375 39.25 34.3867 36.7891 36.8477C34.3672 39.2695 31.4375 40.4805 28 40.4805C24.5625 40.4805 21.6133 39.2695 19.1523 36.8477C16.7305 34.3867 15.5195 31.4375 15.5195 28C15.5195 24.5625 16.7305 21.6328 19.1523 19.2109Z"
                  fill="white" />
              </svg>

            </div>
            <div class="flex  ">
              <svg width="160" height="160" viewBox="0 0 160 160" fill="none" xmlns="http://www.w3.org/2000/svg">
                <g opacity="0.05">
                  <path
                    d="M53.25 96H96V106.75H53.25V96ZM53.25 80H96V90.75H53.25V80ZM53.25 64H96V74.75H53.25V64ZM117.25 26.75V42.75H133.25V53.25H117.25V69.25H106.75V53.25H90.75V42.75H106.75V26.75H117.25ZM106.75 118.5V80H117.25V117.25C117.25 120.083 116.167 122.583 114 124.75C112 126.917 109.583 128 106.75 128H42.75C39.9167 128 37.4167 126.917 35.25 124.75C33.0833 122.583 32 120.083 32 117.25V53.25C32 50.4167 33.0833 48 35.25 46C37.4167 43.8333 39.9167 42.75 42.75 42.75H80V53.25H42.75V118.5H106.75Z"
                    fill="#0F172A" />
                </g>
              </svg>

            </div>
          </div>
          <div class="section-content">
            <h3 class="section-card-title">Generate Fee</h3>
            <p class="section-card-description">Create new invoices for entire classes, batches, or individual students
              in just a few clicks.</p>
          </div>
        </div> -->

        <div class="fee-section-card glass  flex flex-col " @click="goToGenerateChallan">
          <!-- Top Row -->
          <div class="flex justify-between items-start">
            <!-- Main Icon -->
            <div class="section-icon structure-icon pr-[250px]   ">
              <svg width="56" height="56" viewBox="0 0 56 56" fill="none" xmlns="http://www.w3.org/2000/svg">
                <rect width="56" height="56" rx="24" fill="#5B13EC" />
                <path
                  d="M34.2695 29.2305V26.7695H29.2305V21.7305H26.7695V26.7695H21.7305V29.2305H26.7695V34.2695H29.2305V29.2305H34.2695ZM19.1523 19.2109C21.6133 16.75 24.5625 15.5195 28 15.5195C31.4375 15.5195 34.3672 16.75 36.7891 19.2109C39.25 21.6328 40.4805 24.5625 40.4805 28C40.4805 31.4375 39.25 34.3867 36.7891 36.8477C34.3672 39.2695 31.4375 40.4805 28 40.4805C24.5625 40.4805 21.6133 39.2695 19.1523 36.8477C16.7305 34.3867 15.5195 31.4375 15.5195 28C15.5195 24.5625 16.7305 21.6328 19.1523 19.2109Z"
                  fill="white" />
              </svg>
            </div>

            <!-- Background Icon -->
            <div class="absolute top-1 right-2 ">
              <svg width="160" height="160" viewBox="0 0 160 160" fill="none" xmlns="http://www.w3.org/2000/svg">
                <g opacity="0.05">
                  <path
                    d="M53.25 96H96V106.75H53.25V96ZM53.25 80H96V90.75H53.25V80ZM53.25 64H96V74.75H53.25V64ZM117.25 26.75V42.75H133.25V53.25H117.25V69.25H106.75V53.25H90.75V42.75H106.75V26.75H117.25ZM106.75 118.5V80H117.25V117.25C117.25 120.083 116.167 122.583 114 124.75C112 126.917 109.583 128 106.75 128H42.75C39.9167 128 37.4167 126.917 35.25 124.75C33.0833 122.583 32 120.083 32 117.25V53.25C32 50.4167 33.0833 48 35.25 46C37.4167 43.8333 39.9167 42.75 42.75 42.75H80V53.25H42.75V118.5H106.75Z"
                    fill="#0F172A" />
                </g>
              </svg>
            </div>
          </div>

          <!-- Content -->
          <div class="p-6">
            <div class="section-content">
              <h3 class="section-card-title">Generate Fee</h3>
              <p class="section-card-description ">Create new invoices for entire classes, batches, or individual
                students in just a few clicks.</p>
            </div>

            <div>
              <button class="inline-flex items-center gap-2 pt-4 text-[#5B13EC] justify-center font-bold">
                Get Started
                <div>
                  <svg width="17" height="17" viewBox="0 0 17 17" fill="none" xmlns="http://www.w3.org/2000/svg">
                    <path
                      d="M8.01562 0L16.0312 8.01562L8.01562 16.0312L6.60938 14.625L12.1875 9H0V7.03125H12.1875L6.60938 1.40625L8.01562 0Z"
                      fill="#5B13EC" />
                  </svg>
                </div>
              </button>
              <div>


              </div>
            </div>
          </div>
        </div>


        <!-- Pay Fee Module -->
        <div class="fee-section-card glass  flex flex-col " @click="goToPayFee">
          <!-- Top Row -->
          <div class="flex justify-between items-start">
            <!-- Main Icon -->
            <div class="section-icon collection-icon pr-[250px]   ">
              <svg width="56" height="56" viewBox="0 0 56 56" fill="none" xmlns="http://www.w3.org/2000/svg">
                <rect width="56" height="56" rx="24" fill="#10B981" />
                <path
                  d="M31.6328 29.3477C32.0234 29.6992 32.4727 29.875 32.9805 29.875C33.4883 29.875 33.918 29.6992 34.2695 29.3477C34.6602 28.9961 34.8555 28.5469 34.8555 28C34.8555 27.4531 34.6602 27.0039 34.2695 26.6523C33.918 26.3008 33.4883 26.125 32.9805 26.125C32.4727 26.125 32.0234 26.3008 31.6328 26.6523C31.2812 27.0039 31.1055 27.4531 31.1055 28C31.1055 28.5469 31.2812 28.9961 31.6328 29.3477ZM28 32.9805V23.0195H40.4805V32.9805H28ZM39.25 35.5V36.7305C39.25 37.3945 38.9961 37.9805 38.4883 38.4883C37.9805 38.9961 37.3945 39.25 36.7305 39.25H19.2695C18.5664 39.25 17.9609 39.0156 17.4531 38.5469C16.9844 38.0391 16.75 37.4336 16.75 36.7305V19.2695C16.75 18.5664 16.9844 17.9805 17.4531 17.5117C17.9609 17.0039 18.5664 16.75 19.2695 16.75H36.7305C37.3945 16.75 37.9805 17.0039 38.4883 17.5117C38.9961 18.0195 39.25 18.6055 39.25 19.2695V20.5H28C27.2969 20.5 26.6914 20.7539 26.1836 21.2617C25.7148 21.7305 25.4805 22.3164 25.4805 23.0195V32.9805C25.4805 33.6836 25.7148 34.2891 26.1836 34.7969C26.6914 35.2656 27.2969 35.5 28 35.5H39.25Z"
                  fill="white" />
              </svg>

            </div>

            <!-- Background Icon -->
            <div class="absolute top-1 right-2 ">
              <svg width="160" height="160" viewBox="0 0 160 160" fill="none" xmlns="http://www.w3.org/2000/svg">
                <g opacity="0.05">
                  <path
                    d="M117.25 90.75C117.25 93.5833 116.167 96.0833 114 98.25C112 100.25 109.583 101.25 106.75 101.25H32C29 101.25 26.4167 100.25 24.25 98.25C22.25 96.0833 21.25 93.5833 21.25 90.75V48C21.25 45 22.25 42.5 24.25 40.5C26.4167 38.3333 29 37.25 32 37.25H106.75C109.583 37.25 112 38.3333 114 40.5C116.167 42.5 117.25 45 117.25 48V90.75ZM69.25 85.25C72.25 85.25 74.9167 84.5833 77.25 83.25C79.75 81.75 81.6667 79.8333 83 77.5C84.5 75 85.25 72.25 85.25 69.25C85.25 66.4167 84.5 63.8333 83 61.5C81.6667 59 79.75 57 77.25 55.5C74.9167 54 72.25 53.25 69.25 53.25C66.4167 53.25 63.75 54 61.25 55.5C58.9167 57 57 59 55.5 61.5C54 63.8333 53.25 66.4167 53.25 69.25C53.25 72.25 54 75 55.5 77.5C57 79.8333 58.9167 81.75 61.25 83.25C63.75 84.5833 66.4167 85.25 69.25 85.25ZM138.75 53.25H128V112H37.25V122.75H128C131 122.75 133.5 121.75 135.5 119.75C137.667 117.583 138.75 115 138.75 112V53.25Z"
                    fill="#0F172A" />
                </g>
              </svg>

            </div>
          </div>

          <!-- Content -->
          <div class="p-6">
            <div class="section-content">
              <h3 class="section-card-title">Pay Fee</h3>
              <p class="section-card-description ">Securely process student payments via cash, credit cards, or bank
                transfers with instant receipts.</p>
            </div>

            <div>
              <button class="inline-flex items-center gap-2 pt-4 text-[#059669] justify-center font-bold">
                Process Payment
                <div>
                  <svg width="17" height="17" viewBox="0 0 17 17" fill="none" xmlns="http://www.w3.org/2000/svg">
                    <path
                      d="M8.01562 0L16.0312 8.01562L8.01562 16.0312L6.60938 14.625L12.1875 9H0V7.03125H12.1875L6.60938 1.40625L8.01562 0Z"
                      fill="#059669" />
                  </svg>
                </div>
              </button>
              <div>


              </div>
            </div>
          </div>
        </div>

        <!-- <div class="fee-section-card glass" @click="goToPayFee">
          <div class="section-icon collection-icon ">
            <svg width="48" height="48" viewBox="0 0 48 48" fill="none">
              <rect width="48" height="48" rx="24" fill="#D1F7E6" />
              <g>
                <rect x="16" y="20" width="16" height="8" rx="2" fill="#fff" />
                <path d="M20 24h8" stroke="#1DB67D" stroke-width="2" stroke-linecap="round" />
                <circle cx="24" cy="24" r="8" stroke="#1DB67D" stroke-width="2" fill="none" />
              </g>
            </svg>
          </div>
          <div class="section-content">
            <h3 class="section-card-title">Pay Fee</h3>
            <p class="section-card-description">Browse, search, and manage all generated fees.</p>
          </div>
        </div> -->


        <!-- Fee Reports & Analytics Module -->
        <div class="fee-section-card glass  flex flex-col " @click="goToSection('reports')">
          <!-- Top Row -->
          <div class="flex justify-between items-start">
            <!-- Main Icon -->
            <div class="section-icon reports-icon pr-[250px]   ">
              <svg width="56" height="56" viewBox="0 0 56 56" fill="none" xmlns="http://www.w3.org/2000/svg">
                <rect width="56" height="56" rx="24" fill="#F59E0B" />
                <path
                  d="M36.7305 16.75C37.4336 16.75 38.0195 17.0039 38.4883 17.5117C38.9961 17.9805 39.25 18.5664 39.25 19.2695V36.7305C39.25 37.4336 38.9961 38.0391 38.4883 38.5469C38.0195 39.0156 37.4336 39.25 36.7305 39.25H19.2695C18.5664 39.25 17.9609 39.0156 17.4531 38.5469C16.9844 38.0391 16.75 37.4336 16.75 36.7305V19.2695C16.75 18.5664 16.9844 17.9805 17.4531 17.5117C17.9609 17.0039 18.5664 16.75 19.2695 16.75H36.7305ZM24.25 34.2695V28H21.7305V34.2695H24.25ZM29.2305 34.2695V30.5195H26.7695V34.2695H29.2305ZM29.2305 28V25.4805H26.7695V28H29.2305ZM34.2695 34.2695V21.7305H31.75V34.2695H34.2695Z"
                  fill="white" />
              </svg>

            </div>

            <!-- Background Icon -->
            <div class="absolute top-2 right-3 ">
              <svg width="160" height="160" viewBox="0 0 160 160" fill="none" xmlns="http://www.w3.org/2000/svg">
                <g opacity="0.05">
                  <path
                    d="M122.75 32C125.583 32 128 33.0833 130 35.25C132.167 37.25 133.25 39.75 133.25 42.75V101.25C133.25 104.25 132.167 106.833 130 109C128 111 125.583 112 122.75 112H106.75L112 117.25V128H48V117.25L53.25 112H37.25C34.4167 112 31.9167 111 29.75 109C27.75 106.833 26.75 104.25 26.75 101.25V42.75C26.75 39.75 27.75 37.25 29.75 35.25C31.9167 33.0833 34.4167 32 37.25 32H122.75ZM122.75 101.25V42.75H37.25V101.25H122.75Z"
                    fill="#0F172A" />
                </g>
              </svg>

            </div>
          </div>

          <!-- Content -->
          <div class="p-6">
            <div class="section-content">
              <h3 class="section-card-title">Reports & Analytics</h3>
              <p class="section-card-description ">Access detailed collection trends, financial statements, and track
                defaulting accounts in real-time.</p>
            </div>

            <div>
              <button class="inline-flex items-center gap-2 pt-4 text-[#D97706] justify-center font-bold">
                View Analysis
                <div>
                  <svg width="17" height="17" viewBox="0 0 17 17" fill="none" xmlns="http://www.w3.org/2000/svg">
                    <path
                      d="M8.01562 0L16.0312 8.01562L8.01562 16.0312L6.60938 14.625L12.1875 9H0V7.03125H12.1875L6.60938 1.40625L8.01562 0Z"
                      fill="#D97706" />
                  </svg>
                </div>
              </button>
              <div>


              </div>
            </div>
          </div>
        </div>

        <!-- <div class="fee-section-card glass" @click="goToSection('reports')">
          <div class="section-icon reports-icon">
            <svg width="48" height="48" viewBox="0 0 48 48" fill="none">
              <rect width="48" height="48" rx="24" fill="#FFE7C2" />
              <path d="M32 32H16V16H32V32Z" stroke="#FF9800" stroke-width="2" />
              <path d="M20 24L24 28L32 20" stroke="#FF9800" stroke-width="2" stroke-linecap="round"
                stroke-linejoin="round" />
            </svg>
          </div>
          <div class="section-content">
            <h3 class="section-card-title">Fee Reports & Analytics</h3>
            <p class="section-card-description">View comprehensive reports, analytics, and export fee data for insights.
            </p>
          </div>
        </div> -->
      </div>
    </div>

    <!-- Dynamic Content Area - Removed as not needed -->

    <div class="bg-white rounded-2xl border border-slate-200">
      <!-- Header -->
      <div class="flex items-center justify-between px-6 py-4 font-inter border-[#E2E8F0]">
        <div class="flex items-center gap-2">
          <div class=" flex items-center justify-center">
            <svg width="21" height="18" viewBox="0 0 21 18" fill="none" xmlns="http://www.w3.org/2000/svg">
              <path
                d="M11.0156 5.01562H12.5156V9.23438L16.0312 11.3438L15.2812 12.5625L11.0156 9.98438V5.01562ZM5.625 2.625C7.40625 0.875 9.53125 0 12 0C14.4688 0 16.5781 0.875 18.3281 2.625C20.1094 4.375 21 6.5 21 9C21 11.5 20.1094 13.625 18.3281 15.375C16.5781 17.125 14.4688 18 12 18C10.9688 18 9.82812 17.75 8.57812 17.25C7.35938 16.7188 6.39062 16.0938 5.67188 15.375L7.07812 13.9219C8.45312 15.2969 10.0938 15.9844 12 15.9844C13.9375 15.9844 15.5938 15.3125 16.9688 13.9688C18.3438 12.5938 19.0312 10.9375 19.0312 9C19.0312 7.0625 18.3438 5.42188 16.9688 4.07812C15.5938 2.70313 13.9375 2.01562 12 2.01562C10.0625 2.01562 8.40625 2.70313 7.03125 4.07812C5.6875 5.42188 5.01562 7.0625 5.01562 9H8.01562L3.98438 13.0312L3.89062 12.8906L0 9H3C3 6.5 3.875 4.375 5.625 2.625Z"
                fill="#5B13EC" />
            </svg>

          </div>
          <h2 class="text-lg  font-bold text-[#0F172A]">
            Recent Fee Transactions
          </h2>
        </div>

        <button class="text-sm font-bold text-[#5B13EC] hover:underline">
          View All Records
        </button>
      </div>

      <!-- Table -->
      <div class="overflow-x-auto">
        <table class="w-full text-sm">
          <thead class="bg-[#F8FAFC] text-sm text-[#94A3B8]">
            <tr>
              <th class="px-6 py-3 text-left font-bold">Student Name</th>
              <th class="px-6 py-3 text-left font-bold">Reference No.</th>
              <th class="px-6 py-3 text-left font-bold">Fee Category</th>
              <th class="px-6 py-3 text-left font-bold">Amount</th>
              <th class="px-6 py-3 text-left font-bold">Status</th>
              <th class="px-6 py-3 text-center font-bold">Actions</th>
            </tr>
          </thead>

          <tbody class="divide-y divide-slate-100">
            <tr v-for="item in transactions" :key="item.ref" class="hover:bg-slate-50">
              <!-- Student -->
              <td class="px-6 py-4">
                <div class="flex items-center gap-3">
                  <div class="w-10 h-10 rounded-full bg-slate-200"></div>
                  <div>
                    <p class="text-[#0F172A] font-bold">{{ item.name }}</p>
                    <p class="text-xs text-[#94A3B8] font-normal">{{ item.class }}</p>
                  </div>
                </div>
              </td>

              <!-- Reference -->
              <td class="px-6 py-4 text-[#64748B] font-normal">
                {{ item.ref }}
              </td>

              <!-- Category -->
              <td class="px-6 py-4 text-[#0F172A] font-normal">
                {{ item.category }}
              </td>

              <!-- Amount -->
              <td class="px-6 py-4 font-bold  text-slate-900">
                {{ item.amount }}
              </td>

              <!-- Status -->
              <td class="px-6 py-4">
                <span :class="item.status === 'Paid'
                  ? 'bg-[#D1FAE5] text-[#047857]'
                  : 'bg-[#FEF3C7] text-[#B45309]'" class="px-3 py-1 rounded-full text-xs font-medium">
                  {{ item.status }}
                </span>
              </td>

              <!-- Action -->
              <td class="px-6 py-4 text-center">
                <button class=" hover:text-purple-600">
                  <svg width="17" height="12" viewBox="0 0 17 12" fill="none" xmlns="http://www.w3.org/2000/svg">
                    <path
                      d="M6.67969 4.04297C7.125 3.59766 7.65234 3.375 8.26172 3.375C8.87109 3.375 9.39844 3.59766 9.84375 4.04297C10.2891 4.48828 10.5117 5.01562 10.5117 5.625C10.5117 6.23438 10.2891 6.76172 9.84375 7.20703C9.39844 7.65234 8.87109 7.875 8.26172 7.875C7.65234 7.875 7.125 7.65234 6.67969 7.20703C6.23438 6.76172 6.01172 6.23438 6.01172 5.625C6.01172 5.01562 6.23438 4.48828 6.67969 4.04297ZM5.58984 8.29688C6.33984 9.02344 7.23047 9.38672 8.26172 9.38672C9.29297 9.38672 10.1719 9.02344 10.8984 8.29688C11.6484 7.54688 12.0234 6.65625 12.0234 5.625C12.0234 4.59375 11.6484 3.71484 10.8984 2.98828C10.1719 2.23828 9.29297 1.86328 8.26172 1.86328C7.23047 1.86328 6.33984 2.23828 5.58984 2.98828C4.86328 3.71484 4.5 4.59375 4.5 5.625C4.5 6.65625 4.86328 7.54688 5.58984 8.29688ZM3.23438 1.54688C4.73438 0.515625 6.41016 0 8.26172 0C10.1133 0 11.7891 0.515625 13.2891 1.54688C14.7891 2.57812 15.8672 3.9375 16.5234 5.625C15.8672 7.3125 14.7891 8.67188 13.2891 9.70312C11.7891 10.7344 10.1133 11.25 8.26172 11.25C6.41016 11.25 4.73438 10.7344 3.23438 9.70312C1.73438 8.67188 0.65625 7.3125 0 5.625C0.65625 3.9375 1.73438 2.57812 3.23438 1.54688Z"
                      fill="#94A3B8" />
                  </svg>

                </button>
              </td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>

    <div class="flex pt-4 gap-4">
      <div class=" bg-[#5B13EC0D] border border-[#5B13EC1A] flex gap-2 rounded-3xl  p-6 ">
        <!-- Header -->
        <div>
          <svg width="24" height="59" viewBox="0 0 24 59" fill="none" xmlns="http://www.w3.org/2000/svg">
            <path
              d="M7.03125 5.39062C8.40625 4.01563 10.0625 3.32812 12 3.32812C13.9375 3.32812 15.5781 4.01563 16.9219 5.39062C18.2969 6.73438 18.9844 8.375 18.9844 10.3125C18.9844 12.6562 17.9844 14.5625 15.9844 16.0312V18.3281C15.9844 18.6094 15.8906 18.8438 15.7031 19.0312C15.5156 19.2188 15.2812 19.3125 15 19.3125H9C8.71875 19.3125 8.48438 19.2188 8.29688 19.0312C8.10938 18.8438 8.01562 18.6094 8.01562 18.3281V16.0312C6.01562 14.6562 5.01562 12.75 5.01562 10.3125C5.01562 8.375 5.6875 6.73438 7.03125 5.39062ZM9 22.3125V21.3281H15V22.3125C15 22.5938 14.9062 22.8281 14.7188 23.0156C14.5312 23.2031 14.2969 23.2969 14.0156 23.2969H9.98438C9.70312 23.2969 9.46875 23.2031 9.28125 23.0156C9.09375 22.8281 9 22.5938 9 22.3125Z"
              fill="#5B13EC" />
          </svg>

        </div>
        <div class="flex flex-col gap-2 ">
          <h2 class="text-[#0F172A] font-bold font-inter text-sm align-middel"> Pro Tip: Automated Reminders</h2>
          <p class="text-xs leading-5 text-[#64748B] font-medium">
            You can set up automated SMS and Email reminders for pending fee payments in the Settings menu to increase
            collection rates.
          </p>
        </div>


      </div>

       <div class=" bg-[#F8FAFC] border border-[#5B13EC1A] flex gap-2 rounded-3xl  p-6 ">
        <!-- Header -->
        <div>
         <svg width="24" height="59" viewBox="0 0 24 59" fill="none" xmlns="http://www.w3.org/2000/svg">
<path d="M21 13.5469C21.2812 13.7031 21.5156 13.9219 21.7031 14.2031C21.8906 14.4844 21.9844 14.7969 21.9844 15.1406V17.4375C21.9844 17.8125 21.8906 18.1406 21.7031 18.4219C21.5156 18.7031 21.2812 18.9219 21 19.0781V20.2969C21 20.8594 20.7969 21.3438 20.3906 21.75C20.0156 22.125 19.5469 22.3125 18.9844 22.3125H11.0156V20.2969H18.9844V13.2188C18.9844 12.25 18.7969 11.3438 18.4219 10.5C18.0781 9.65625 17.5781 8.92188 16.9219 8.29688C16.2969 7.64062 15.5625 7.14062 14.7188 6.79688C13.875 6.42188 12.9688 6.23438 12 6.23438C11.0312 6.23438 10.125 6.42188 9.28125 6.79688C8.4375 7.14062 7.6875 7.64062 7.03125 8.29688C6.40625 8.92188 5.90625 9.65625 5.53125 10.5C5.1875 11.3438 5.01562 12.25 5.01562 13.2188V19.3125H3.98438C3.45312 19.3125 2.98438 19.125 2.57812 18.75C2.20312 18.3438 2.01562 17.8594 2.01562 17.2969V15.3281C2.01562 14.9531 2.09375 14.6094 2.25 14.2969C2.4375 13.9844 2.6875 13.75 3 13.5938C3 12.1875 3.23438 10.9219 3.70312 9.79688C4.20312 8.64062 4.875 7.65625 5.71875 6.84375C6.59375 6.03125 7.5625 5.40625 8.625 4.96875C9.6875 4.53125 10.8125 4.3125 12 4.3125C13.1875 4.3125 14.3125 4.53125 15.375 4.96875C16.4688 5.40625 17.4375 6.04688 18.2812 6.89062C19.125 7.70312 19.7812 8.67188 20.25 9.79688C20.75 10.9219 21 12.1719 21 13.5469ZM8.01562 14.2969C8.01562 14.5781 8.10938 14.8281 8.29688 15.0469C8.48438 15.2344 8.71875 15.3281 9 15.3281C9.28125 15.3281 9.51562 15.2344 9.70312 15.0469C9.89062 14.8281 9.98438 14.5781 9.98438 14.2969C9.98438 14.0156 9.89062 13.7812 9.70312 13.5938C9.51562 13.4062 9.28125 13.3125 9 13.3125C8.71875 13.3125 8.48438 13.4062 8.29688 13.5938C8.10938 13.7812 8.01562 14.0156 8.01562 14.2969ZM14.0156 14.2969C14.0156 14.5781 14.1094 14.8281 14.2969 15.0469C14.4844 15.2344 14.7188 15.3281 15 15.3281C15.2812 15.3281 15.5156 15.2344 15.7031 15.0469C15.8906 14.8281 15.9844 14.5781 15.9844 14.2969C15.9844 14.0156 15.8906 13.7812 15.7031 13.5938C15.5156 13.4062 15.2812 13.3125 15 13.3125C14.7188 13.3125 14.4844 13.4062 14.2969 13.5938C14.1094 13.7812 14.0156 14.0156 14.0156 14.2969ZM18 12.3281C16.9688 12.3281 15.9844 12.1406 15.0469 11.7656C14.1406 11.3906 13.3281 10.875 12.6094 10.2188C11.8906 9.53125 11.3125 8.75 10.875 7.875C10.625 9.21875 10.0625 10.4062 9.1875 11.4375C8.3125 12.4688 7.25 13.25 6 13.7812C5.9375 12.7812 6.0625 11.8906 6.375 11.1094C6.71875 10.2969 7.1875 9.60938 7.78125 9.04688C8.375 8.48438 9.04688 8.0625 9.79688 7.78125C10.5469 7.46875 11.2969 7.3125 12.0469 7.3125C13.0469 7.3125 13.9688 7.53125 14.8125 7.96875C15.6562 8.40625 16.3594 9.01562 16.9219 9.79688C17.4844 10.5469 17.8438 11.3906 18 12.3281Z" fill="#94A3B8"/>
</svg>


        </div>
        <div class="flex flex-col gap-2 ">
          <h2 class="text-[#0F172A] font-bold font-inter text-sm align-middle"> Need Help?</h2>
          <p class="text-xs leading-5 text-[#64748B] font-medium">
            You can set up automated SMS and Email reminders for pending fee payments in the Settings menu to increase
            collection rates.
          </p>
        </div>


      </div>
    </div>


  </div>
</template>

<script setup>
import { ref } from 'vue'
import { useRouter } from 'vue-router'
import { useToast } from 'vue-toastification'

const activeTab = ref('review')
const searchQuery = ref('')
const selectedFilter = ref('all')
const dateRange = ref([])
const activeSection = ref(null)
const router = useRouter()
const toast = useToast()


const transactions = [
  {
    name: "Julianna Rodriguez",
    class: "Class 10-B",
    ref: "#INV-2023-0045",
    category: "Tuition Fee",
    amount: "$1,200.00",
    status: "Paid",
  },
  {
    name: "Marcus Chen",
    class: "Class 8-A",
    ref: "#INV-2023-0044",
    category: "Library Fee",
    amount: "$50.00",
    status: "Pending",
  },
  {
    name: "Sophia Wilson",
    class: "Class 12-C",
    ref: "#INV-2023-0043",
    category: "Transportation",
    amount: "$250.00",
    status: "Paid",
  },
];
// ApexCharts data and options
const chartOptions = ref({
  chart: {
    type: 'area',
    toolbar: { show: false },
    background: 'transparent',
    fontFamily: 'Inter, Segoe UI, Arial, sans-serif',
    foreColor: '#64748b',
    sparkline: { enabled: false },
    dropShadow: { enabled: false },
    animations: { enabled: true, easing: 'easeinout', speed: 700 },
    offsetY: 0,
    offsetX: 0,
    stacked: false,
    zoom: { enabled: false },
  },
  colors: ['#fde68a', '#2563eb'],
  dataLabels: { enabled: false },
  stroke: {
    curve: 'smooth',
    width: [4, 2],
    dashArray: [0, 6]
  },
  fill: {
    type: 'gradient',
    gradient: {
      shade: 'light',
      type: 'vertical',
      shadeIntensity: 0.2,
      gradientToColors: ['#fbbf24', '#60a5fa'],
      inverseColors: false,
      opacityFrom: 0.7,
      opacityTo: 0.12,
      stops: [0, 100]
    }
  },
  grid: {
    borderColor: '#e0e7ef',
    strokeDashArray: 5,
    yaxis: { lines: { show: true } },
    xaxis: { lines: { show: false } },
    padding: { left: 0, right: 0, top: 0, bottom: 0 },
  },
  xaxis: {
    categories: ['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun', 'Jul', 'Aug'],
    labels: { style: { colors: '#7b8ca6', fontSize: '15px', fontWeight: 700 } },
    axisBorder: { show: false },
    axisTicks: { show: false },
    offsetX: 0,
  },
  yaxis: {
    labels: { style: { colors: '#7b8ca6', fontSize: '15px', fontWeight: 700 } },
    offsetX: 0,
  },
  legend: {
    show: true,
    position: 'top',
    horizontalAlign: 'right',
    fontSize: '14px',
    fontWeight: 500,
    markers: {
      width: 9,
      height: 9,
      radius: 9,
      offsetX: -2
    },
    labels: { colors: '#a0aec0' },
    itemMargin: { horizontal: 12, vertical: 0 },
    fontFamily: 'Inter, Segoe UI, Arial, sans-serif',
  },
  tooltip: {
    theme: 'light',
    style: { fontSize: '15px', fontWeight: 600, borderRadius: 10, padding: 12, boxShadow: '0 4px 24px rgba(60,72,100,0.13)' },
    marker: { show: true },
    y: {
      formatter: (val, opts) => `${opts.seriesIndex === 0 ? 'Earnings' : 'Expenses'} ${val}K`
    }
  },
  chartArea: {
    background: 'linear-gradient(135deg, #f8fafc 80%, #e0e7ff 100%)',
    opacity: 0.7
  }
})

const series = ref([
  { name: 'Earnings', data: [30, 40, 35, 50, 49, 60, 70, 91] },
  { name: 'Expenses', data: [20, 29, 37, 36, 44, 45, 50, 58] }
])

// Dropdown for months
const monthsOptions = [
  'Last 8 Months',
  'Last 6 Months',
  'Last 12 Months'
]
const selectedMonths = ref(monthsOptions[0])

// Removed dynamic component loading - not needed

const goToSection = (section) => {
  if (section === 'structure') router.push({ name: 'FeeStructure' })
  else if (section === 'collection') router.push({ name: 'FeeCollectionPage' })
  else if (section === 'reports') router.push({ name: 'FeeAnalytics' })
}

const goToGenerateChallan = () => {
  router.push({ name: 'GenerateChallan' })
}

function goToPayFee() {
  router.push({ name: 'PayFee' })
}
</script>

<style scoped>
@keyframes fadeIn {
  from {
    opacity: 0;
    transform: translateY(20px);
  }

  to {
    opacity: 1;
    transform: translateY(0);
  }
}

@keyframes slideInFromTop {
  from {
    opacity: 0;
    transform: translateY(-30px);
  }

  to {
    opacity: 1;
    transform: translateY(0);
  }
}

@keyframes pulseIcon {
  0% {
    transform: scale(1);
  }

  50% {
    transform: scale(1.05);
  }

  100% {
    transform: scale(1);
  }
}

@keyframes float {
  0% {
    transform: translateY(0px);
  }

  50% {
    transform: translateY(-10px);
  }

  100% {
    transform: translateY(0px);
  }
}

@keyframes shimmer {
  0% {
    background-position: -200% center;
  }

  100% {
    background-position: 200% center;
  }
}

.fee-collection-ultra {
  max-width: 1280px;
  margin: 0 auto;
  padding: 36px 12px 36px 12px;
  font-family: 'Inter', 'SF Pro', 'Segoe UI', Arial, sans-serif;
  background: #f7faff;
  animation: fadeIn 0.6s ease-out;
}

.glass {
  background: rgba(255, 255, 255, 0.75);
  backdrop-filter: blur(8px);
  box-shadow: 0 8px 32px 0 rgba(60, 72, 100, 0.10);
  transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
}

.glass:hover {
  transform: translateY(-2px);
  box-shadow: 0 12px 40px 0 rgba(60, 72, 100, 0.15);
}

.ultra-header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  border-radius: 18px;
  padding: 32px 36px 28px 36px;
  margin-bottom: 36px;
  box-shadow: 0 4px 24px rgba(60, 72, 100, 0.08);
  background: linear-gradient(90deg, #f8fafc 80%, #e0e7ff 100%);
  animation: slideInFromTop 0.8s cubic-bezier(0.4, 0, 0.2, 1);
}

.header-left {
  display: flex;
  align-items: center;
  gap: 22px;
}

.header-icon {
  background: #e6edff;
  border-radius: 16px;
  width: 64px;
  height: 64px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 36px;
  color: #3a6ff7;
  box-shadow: 0 2px 8px rgba(99, 102, 241, 0.06);
  animation: pulseIcon 2s infinite;
}

.header-titles {
  display: flex;
  flex-direction: column;
  gap: 6px;
}

.ultra-title {
  font-size: 2.2rem;
  font-weight: 900;
  color: #1e293b;
  margin: 0;
  letter-spacing: 0.5px;
}

.ultra-subtitle {
  font-size: 1.08rem;
  color: #64748b;
  font-weight: 500;
  margin-top: 2px;
}

.header-right {
  display: flex;
  align-items: center;
}

.new-fee-btn {
  font-size: 1.08rem;
  font-weight: 700;
  border-radius: 10px;
  padding: 12px 28px;
  background: linear-gradient(90deg, #6366f1 80%, #a5b4fc 100%);
  color: #ffffff;
  box-shadow: 0 2px 8px rgba(99, 102, 241, 0.10);
  border: none;
  transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
  position: relative;
  overflow: hidden;
}

.new-fee-btn::before {
  content: '';
  position: absolute;
  top: 0;
  left: -100%;
  width: 100%;
  height: 100%;
  background: linear-gradient(90deg,
      transparent,
      #ffffff,
      transparent);
  transition: 0.5s;
}

.new-fee-btn:hover::before {
  left: 100%;
}

.new-fee-btn:hover {
  background: linear-gradient(90deg, #4338ca 80%, #a5b4fc 100%);
  transform: translateY(-2px) scale(1.04);
  box-shadow: 0 8px 24px rgba(99, 102, 241, 0.2);
}

.ultra-stats-row {
  display: flex;
  gap: 32px;
  margin-bottom: 40px;
  flex-wrap: wrap;
  justify-content: space-between;
}

.ultra-stat-card {
  flex: 1 1 0;
  min-width: 260px;
  max-width: 370px;
  display: flex;
  align-items: center;
  gap: 22px;
  border-radius: 18px;
  padding: 32px 32px;
  margin-bottom: 0;
  box-shadow: 0 4px 24px rgba(60, 72, 100, 0.08);
  transition: box-shadow 0.18s, transform 0.18s;
  position: relative;
  background: rgba(255, 255, 255, 0.85);
  border: 1.5px solid #f1f5f9;
}

.ultra-stat-card:hover {
  box-shadow: 0 8px 32px rgba(60, 72, 100, 0.13);
  transform: translateY(-2px) scale(1.02);
}

.stat-icon {
  width: 60px;
  height: 60px;
  border-radius: 16px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 34px;
  box-shadow: 0 2px 8px rgba(99, 102, 241, 0.06);
}

.stat-blue {
  background: linear-gradient(135deg, #e0e7ff 60%, #f8fafc 100%);
}

.stat-green {
  background: linear-gradient(135deg, #d1f7e6 60%, #f8fafc 100%);
}

.stat-orange {
  background: linear-gradient(135deg, #ffe7c2 60%, #f8fafc 100%);
}

.stat-info {
  display: flex;
  flex-direction: column;
  gap: 6px;
}

.stat-label {
  font-size: 1.08rem;
  color: #888;
  font-weight: 600;
}

.stat-value {
  font-size: 2.1rem;
  font-weight: 900;
  color: #181d2f;
  letter-spacing: 1px;
}

.stat-anim {
  /* Placeholder for animated numbers */
}

.stat-growth {
  font-size: 1rem;
  color: #1db67d;
  font-weight: 600;
  margin-top: 2px;
}

.stat-growth.up {
  color: #1db67d;
}

.ultra-tabs-row {
  margin-top: 18px;
  background: transparent;
}

.ultra-tabs {
  --el-tabs-header-height: 52px;
  --el-tabs-item-font-size: 1.08rem;
  --el-tabs-item-font-weight: 700;
  --el-tabs-item-border-radius: 16px 16px 0 0;
  --el-tabs-item-padding: 0 36px;
}

.ultra-tabs .el-tabs__item {
  font-size: 1.08rem;
  font-weight: 700;
  border-radius: 16px 16px 0 0;
  padding: 0 36px;
  color: #64748b;
  transition: color 0.18s, background 0.18s;
  background: transparent;
}

.ultra-tabs .el-tabs__item.is-active {
  color: #8b5cf6;
  background: #f8fafc;
  font-weight: 900;
  border-bottom: 3px solid #6366f1;
}

.ultra-tab-content {
  padding: 56px 0 0 0;
  min-height: 260px;
  display: flex;
  align-items: center;
  justify-content: center;
}

.ultra-empty-state {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 22px;
  color: #94a3b8;
}

.empty-illustration {
  width: 130px;
  opacity: 0.88;
  margin-bottom: 8px;
}

.empty-message {
  font-size: 1.18rem;
  color: #94a3b8;
  font-weight: 600;
}

.cta-btn {
  font-size: 1.08rem;
  font-weight: 700;
  border-radius: 10px;
  padding: 10px 28px;
  background: linear-gradient(90deg, #6366f1 80%, #a5b4fc 100%);
  color: #ffffff;
  box-shadow: 0 2px 8px rgba(99, 102, 241, 0.10);
  border: none;
  transition: background 0.18s, box-shadow 0.18s, transform 0.18s;
}

.cta-btn:hover {
  background: linear-gradient(90deg, #4338ca 80%, #a5b4fc 100%);
  transform: translateY(-2px) scale(1.04);
  box-shadow: 0 4px 16px rgba(99, 102, 241, 0.13);
}

@media (max-width: 900px) {
  .ultra-header {
    flex-direction: column;
    align-items: flex-start;
    padding: 22px 10px 18px 10px;
    gap: 10px;
  }

  .ultra-stats-row {
    flex-direction: column;
    gap: 18px;
  }

  .ultra-stat-card {
    min-width: 0;
    max-width: 100vw;
    padding: 18px 12px;
    gap: 10px;
    min-height: 100px;
  }

  .stat-value {
    font-size: 1.4rem;
  }

  .ultra-title {
    font-size: 1.3rem;
  }
}

/* New Modern Styles */
.search-filter-section {
  display: flex;
  gap: 20px;
  padding: 24px;
  border-radius: 18px;
  margin-bottom: 32px;
  align-items: center;
  flex-wrap: wrap;
}

.search-box {
  flex: 1;
  min-width: 300px;
}

.modern-search :deep(.el-input__wrapper) {
  background: #ffffff;
  border-radius: 12px;
  box-shadow: 0 2px 12px rgba(0, 0, 0, 0.04);
  padding: 8px 16px;
  transition: all 0.3s ease;
}

.modern-search :deep(.el-input__wrapper:hover) {
  box-shadow: 0 4px 16px rgba(0, 0, 0, 0.08);
}

.filter-options {
  display: flex;
  gap: 16px;
  flex-wrap: wrap;
}

.modern-select :deep(.el-input__wrapper) {
  background: #ffffff;
  border-radius: 12px;
  box-shadow: 0 2px 12px rgba(0, 0, 0, 0.04);
}

.modern-datepicker :deep(.el-input__wrapper) {
  background: #ffffff;
  border-radius: 12px;
  box-shadow: 0 2px 12px rgba(0, 0, 0, 0.04);
}

/* Animations */
.animate-in {
  animation: slideIn 0.5s ease-out forwards;
  opacity: 0;
  transform: translateY(20px);
}

@keyframes slideIn {
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.pulse {
  animation: pulse 2s infinite;
}

@keyframes pulse {
  0% {
    transform: scale(1);
  }

  50% {
    transform: scale(1.05);
  }

  100% {
    transform: scale(1);
  }
}

.floating {
  animation: floating 3s ease-in-out infinite;
}

@keyframes floating {
  0% {
    transform: translateY(0px);
  }

  50% {
    transform: translateY(-10px);
  }

  100% {
    transform: translateY(0px);
  }
}

.empty-illustration-container {
  position: relative;
  margin-bottom: 24px;
}

.empty-glow {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  width: 200px;
  height: 200px;
  background: radial-gradient(circle, rgba(99, 102, 241, 0.15) 0%, rgba(99, 102, 241, 0) 70%);
  border-radius: 50%;
  z-index: -1;
}

.empty-description {
  color: #94a3b8;
  font-size: 1rem;
  margin: 8px 0 24px;
  text-align: center;
}

.btn-icon {
  margin-right: 8px;
}

.pulse-btn {
  animation: buttonPulse 2s infinite;
}

@keyframes buttonPulse {
  0% {
    box-shadow: 0 0 0 0 rgba(99, 102, 241, 0.4);
  }

  70% {
    box-shadow: 0 0 0 10px rgba(99, 102, 241, 0);
  }

  100% {
    box-shadow: 0 0 0 0 rgba(99, 102, 241, 0);
  }
}

/* Enhanced Responsive Design */
@media (max-width: 900px) {
  .search-filter-section {
    flex-direction: column;
    padding: 16px;
  }

  .search-box {
    width: 100%;
  }

  .filter-options {
    width: 100%;
  }

  .modern-select,
  .modern-datepicker {
    width: 100%;
  }
}

/* Fee Sections Styles */
.fee-sections-container {
  margin: 40px 0;
}

.section-header {
  margin-bottom: 24px;
  flex-wrap: flex;
}

.section-title {
  font-size: 1.8rem;
  font-weight: 700;
  color: #1e293b;
  margin: 0;
}

.section-subtitle {
  font-size: 1.1rem;
  color: #64748b;
  margin-top: 8px;
}

.fee-sections-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 24px;
  margin-top: 24px;
}

.fee-section-card {
  display: flex;
  align-items: center;
  padding: 24px;
  border-radius: 16px;
  cursor: pointer;
  transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
  position: relative;
  overflow: hidden;
  border: 1.5px solid #ffffff;
  animation: fadeIn 0.6s ease-out forwards;
  opacity: 0;
}

.fee-section-card:nth-child(1) {
  animation-delay: 0.2s;
}

.fee-section-card:nth-child(2) {
  animation-delay: 0.3s;
}

.fee-section-card:nth-child(3) {
  animation-delay: 0.4s;
}

.fee-section-card:hover {
  transform: translateY(-8px) scale(1.02);
  box-shadow: 0 16px 40px rgba(60, 72, 100, 0.15);
}

.section-icon {
  flex-shrink: 0;
  margin-right: 20px;
  animation: float 3s ease-in-out infinite;
}

.section-content {
  flex: 1;
}

.section-card-title {
  font-size: 1.2rem;
  font-weight: 700;
  color: #1e293b;
  margin: 0 0 8px 0;
}

.section-card-description {
  font-size: 0.95rem;
  color: #64748b;
  margin: 0;
  line-height: 1.5;
  justify-content: space-between;
}

.section-arrow {
  color: #8b5cf6;
  font-size: 1.2rem;
  opacity: 0;
  transform: translateX(-10px);
  transition: all 0.3s ease;
}

.fee-section-card:hover .section-arrow {
  opacity: 1;
  transform: translateX(0);
}

.dynamic-content-area {
  margin-top: 32px;
  padding: 32px;
  border-radius: 16px;
  min-height: 400px;
}

/* Responsive Adjustments */
@media (max-width: 768px) {
  .fee-sections-grid {
    grid-template-columns: 1fr;
  }

  .fee-section-card {
    padding: 20px;
  }

  .section-icon {
    margin-right: 16px;
  }

  .section-card-title {
    font-size: 1.1rem;
  }

  .section-card-description {
    font-size: 0.9rem;
  }
}

.fee-dashboard-cards {
  width: 100%;
  max-width: 1400px;
  margin: 0 auto;
  padding: 32px 0;
  display: flex;
  flex-direction: column;
  align-items: center;
}

.fee-cards-row {
  display: flex;
  flex-wrap: wrap;
  gap: 32px;
  justify-content: center;
  width: 100%;
}

.fee-card {
  border-radius: 18px;
  box-shadow: 0 4px 24px rgba(60, 72, 100, 0.10);
  background: #fff;
  min-width: 220px;
  max-width: 260px;
  width: 100%;
  padding: 16px 14px 14px 14px;
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  position: relative;
  transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
  animation: fadeIn 0.6s ease-out forwards;
  opacity: 0;
}

.fee-card:nth-child(1) {
  animation-delay: 0.1s;
}

.fee-card:nth-child(2) {
  animation-delay: 0.2s;
}

.fee-card:nth-child(3) {
  animation-delay: 0.3s;
}

.fee-card:nth-child(4) {
  animation-delay: 0.4s;
}

.fee-card:hover {
  box-shadow: 0 12px 40px rgba(60, 72, 100, 0.16);
  transform: translateY(-8px) scale(1.02);
}

.fee-card::after {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  border-radius: 18px;
  background: linear-gradient(45deg, rgba(255, 255, 255, 0.1), rgba(255, 255, 255, 0));
  opacity: 0;
  transition: opacity 0.3s ease;
}

.fee-card:hover::after {
  opacity: 1;
}

.fee-card-value {
  font-size: 1.1rem;
  font-weight: 800;
  margin-bottom: 4px;
  margin-top: 2px;
  letter-spacing: 0.3px;
}

.fee-card-split {
  display: flex;
  flex-direction: row;
  min-width: 600px;
  max-width: 700px;
  padding: 0;
  background: none;
  box-shadow: none;
}

.fee-card-half {
  flex: 1;
  padding: 16px 14px 14px 14px;
  border-radius: 18px;
  margin: 0 4px;
  background: #fff;
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  box-shadow: 0 4px 24px rgba(60, 72, 100, 0.10);
  position: relative;
  transition: box-shadow 0.18s, transform 0.18s;
}

.fee-card-half:first-child {
  margin-left: 0;
}

.fee-card-half:last-child {
  margin-right: 0;
}

.fee-card-half:hover {
  box-shadow: 0 8px 32px rgba(60, 72, 100, 0.16);
  transform: translateY(-4px) scale(1.03);
}

.fee-card-blue {
  background: linear-gradient(135deg, #2563eb 80%, #60a5fa 100%);
  color: #ffffff;
}

.fee-card-blue .fee-card-title,
.fee-card-blue .fee-card-value,
.fee-card-blue .fee-card-link {
  color: #ffffff;
}

.fee-card-green {
  background: linear-gradient(135deg, #059669 80%, #34d399 100%);
  color: #ffffff;
}

.fee-card-green .fee-card-title,
.fee-card-green .fee-card-value,
.fee-card-green .fee-card-link {
  color: #ffffff;
}

.fee-card-purple {
  background: linear-gradient(135deg, #a21caf 80%, #c084fc 100%);
  color: #ffffff;
}

.fee-card-purple .fee-card-title,
.fee-card-purple .fee-card-value,
.fee-card-purple .fee-card-link {
  color: #ffffff;
}

.fee-card-orange {
  background: linear-gradient(135deg, #f59e42 80%, #fbbf24 100%);
  color: #ffffff;
}

.fee-card-orange .fee-card-title,
.fee-card-orange .fee-card-value,
.fee-card-orange .fee-card-link {
  color: #ffffff;
}

.fee-card-yellow {
  background: linear-gradient(135deg, #fbbf24 80%, #fde68a 100%);
  color: #ffffff;
}

.fee-card-yellow .fee-card-title,
.fee-card-yellow .fee-card-value,
.fee-card-yellow .fee-card-link {
  color: #ffffff;
}

.fee-card-header {
  display: flex;
  align-items: center;
  gap: 8px;
  margin-bottom: 8px;
}

.fee-card-icon {
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 1.3rem;
}

.fee-card-title {
  font-size: 0.95rem;
  font-weight: 700;
  letter-spacing: 0.1px;
}

.fee-card-link {
  font-size: 1rem;
  color: #ffffff;
  text-decoration: underline;
  opacity: 0.9;
  transition: opacity 0.18s;
}

.fee-card-link:hover {
  opacity: 1;
}

@media (max-width: 1200px) {
  .fee-cards-row {
    flex-direction: column;
    align-items: center;
  }

  .fee-card,
  .fee-card-split {
    min-width: 320px;
    max-width: 98vw;
  }
}

@media (max-width: 700px) {
  .fee-card-split {
    flex-direction: column;
    min-width: 0;
    max-width: 98vw;
  }

  .fee-card-half {
    margin: 8px 0;
    width: 100%;
  }
}

.chart-card,
.chart-card.glass-blur {
  border-radius: 20px;
  padding: 24px 24px 8px 24px;
  margin-bottom: 32px;
  background: linear-gradient(135deg, #f8fafc 80%, #e0e7ff 100%);
  box-shadow: 0 8px 32px 0 rgba(60, 72, 100, 0.13);
  border: none;
  position: relative;
  backdrop-filter: blur(8px) saturate(1.2);
  -webkit-backdrop-filter: blur(8px) saturate(1.2);
  overflow: visible;
}

.chart-header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-bottom: 8px;
}

.chart-title {
  font-size: 1.18rem;
  font-weight: 800;
  color: #1e293b;
  letter-spacing: 0.1px;
}

.chart-dropdown-wrap {
  position: relative;
  display: flex;
  align-items: center;
}

.chart-dropdown {
  border: none;
  background: #f1f5f9;
  color: #8b5cf6;
  font-weight: 700;
  font-size: 1rem;
  border-radius: 16px;
  padding: 7px 32px 7px 18px;
  box-shadow: 0 2px 8px rgba(99, 102, 241, 0.04);
  outline: none;
  cursor: pointer;
  transition: background 0.18s;
  appearance: none;
  -webkit-appearance: none;
}

.chart-dropdown:focus {
  background: #e0e7ff;
}

.chevron {
  position: absolute;
  right: 14px;
  pointer-events: none;
  color: #8b5cf6;
  font-size: 1.1em;
  top: 50%;
  transform: translateY(-50%);
}

.fee-cards-new-layout {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 28px;
  width: 100%;
}

@media (max-width: 900px) {
  .fee-cards-new-layout {
    grid-template-columns: 1fr;
    gap: 18px;
  }
}

.fee-card-combined {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: stretch;
  min-width: 0;
  min-height: 140px;
  border-radius: 18px;
  box-shadow: 0 4px 24px rgba(60, 72, 100, 0.10);
  padding: 28px 24px 24px 24px;
  background: #2563eb;
  color: #ffffff;
}

.fee-card-blue {
  background: linear-gradient(135deg, #2563eb 80%, #60a5fa 100%);
  color: #ffffff;
}

.fee-card-purple {
  background: linear-gradient(135deg, #a21caf 80%, #c084fc 100%);
  color: #ffffff;
}

.fee-card-yellow {
  background: linear-gradient(135deg, #fbbf24 80%, #fde68a 100%);
  color: #ffffff;
}

.fee-combined-row {
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: 24px;
}

@media (max-width: 600px) {
  .fee-combined-row {
    flex-direction: column;
    gap: 12px;
  }
}

.fee-combined-block {
  flex: 1;
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  justify-content: center;
}

.fee-card-standalone {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: flex-start;
  min-width: 0;
  min-height: 140px;
  border-radius: 18px;
  box-shadow: 0 4px 24px rgba(60, 72, 100, 0.10);
  padding: 28px 24px 24px 24px;
}

.fee-cards-modern {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(290px, 1fr));
  gap: 32px;
  width: 100%;
  margin: 0 auto;
}

@media (max-width: 900px) {
  .fee-cards-modern {
    grid-template-columns: 1fr;
    gap: 18px;
  }
}

.modern-fee-card {
  position: relative;
  border-radius: 22px;
  background: rgba(255, 255, 255, 0.18);
  box-shadow: 0 8px 32px 0 rgba(60, 72, 100, 0.13), 0 1.5px 8px 0 rgba(60, 72, 100, 0.08);
  backdrop-filter: blur(14px) saturate(1.2);
  -webkit-backdrop-filter: blur(14px) saturate(1.2);
  padding: 36px 32px 32px 32px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: stretch;
  min-width: 0;
  min-height: 170px;
  overflow: visible;
  transition: box-shadow 0.22s, transform 0.22s, background 0.22s;
  cursor: pointer;
}

.modern-fee-card:hover {
  box-shadow: 0 16px 48px 0 rgba(60, 72, 100, 0.18), 0 2px 12px 0 rgba(60, 72, 100, 0.10);
  transform: translateY(-6px) scale(1.025);
  background: rgba(255, 255, 255, 0.28);
}

.modern-blue {
  background: linear-gradient(135deg, rgba(37, 99, 235, 0.92) 70%, rgba(96, 165, 250, 0.85) 100%);
  color: #ffffff;
}

.modern-purple {
  background: linear-gradient(135deg, rgba(162, 28, 175, 0.92) 70%, rgba(192, 132, 252, 0.85) 100%);
  color: #ffffff;
}

.modern-yellow {
  background: linear-gradient(135deg, rgba(251, 191, 36, 0.92) 70%, rgba(253, 230, 138, 0.85) 100%);
  color: #ffffff;
}

.modern-card-content {
  display: flex;
  justify-content: space-between;
  align-items: flex-end;
  gap: 32px;
}

.modern-card-content.single {
  justify-content: flex-start;
}

@media (max-width: 600px) {
  .modern-card-content {
    flex-direction: column;
    gap: 18px;
    align-items: flex-start;
  }
}

.modern-card-block {
  flex: 1;
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  justify-content: center;
}

.modern-card-label {
  font-size: 0.98rem;
  font-weight: 700;
  letter-spacing: 0.12em;
  text-transform: uppercase;
  color: #f3f4f6;
  margin-bottom: 6px;
  opacity: 0.92;
}

.modern-card-value {
  font-size: 2.1rem;
  font-weight: 900;
  letter-spacing: 0.5px;
  color: #ffffff;
  line-height: 1.1;
  text-shadow: 0 2px 8px rgba(60, 72, 100, 0.10);
}

.modern-card-glow {
  position: absolute;
  right: -40px;
  bottom: -40px;
  width: 120px;
  height: 120px;
  background: radial-gradient(circle, rgba(255, 255, 255, 0.18) 0%, rgba(255, 255, 255, 0) 80%);
  z-index: 0;
  pointer-events: none;
}

/* Modern Fee Summary Cards Redesign */
.modern-fee-summary-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
  gap: 20px;
  width: 100%;
  max-width: 1400px;
  margin: 0 auto 20px auto;
  padding: 10px 0 0 0;
}

.modern-fee-summary-card {
  position: relative;
  border-radius: 16px;
  background: rgba(255, 255, 255, 0.18);
  box-shadow: 0 8px 32px 0 rgba(60, 72, 100, 0.13), 0 1.5px 8px 0 rgba(60, 72, 100, 0.08);
  backdrop-filter: blur(14px) saturate(1.2);
  -webkit-backdrop-filter: blur(14px) saturate(1.2);
  padding: 18px 14px 14px 14px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: stretch;
  min-width: 0;
  min-height: 80px;
  overflow: visible;
  transition: box-shadow 0.22s, transform 0.22s, background 0.22s;
  cursor: pointer;
  animation: fadeIn 0.7s cubic-bezier(0.4, 0, 0.2, 1);
}

.modern-fee-summary-card:hover {
  box-shadow: 0 16px 48px 0 rgba(60, 72, 100, 0.18), 0 2px 12px 0 rgba(60, 72, 100, 0.10);
  transform: translateY(-8px) scale(1.03);
  background: rgba(255, 255, 255, 0.28);
}

.modern-blue {
  background: linear-gradient(135deg, rgba(37, 99, 235, 0.96) 70%, rgba(96, 165, 250, 0.90) 100%);
  color: #ffffff;
}

.modern-purple {
  background: linear-gradient(135deg, rgba(162, 28, 175, 0.96) 70%, rgba(192, 132, 252, 0.90) 100%);
  color: #ffffff;
}

.modern-yellow {
  background: linear-gradient(135deg, rgba(251, 191, 36, 0.96) 70%, rgba(253, 230, 138, 0.90) 100%);
  color: #ffffff;
}

.modern-fee-summary-content {
  display: flex;
  justify-content: space-between;
  align-items: flex-end;
  gap: 36px;
}

.modern-fee-summary-content.single {
  justify-content: flex-start;
}

@media (max-width: 600px) {
  .modern-fee-summary-content {
    flex-direction: column;
    gap: 18px;
    align-items: flex-start;
  }
}

.modern-fee-summary-block {
  flex: 1;
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  justify-content: center;
}

.modern-fee-summary-label {
  font-size: 0.92rem;
  font-weight: 700;
  letter-spacing: 0.13em;
  text-transform: uppercase;
  color: #f3f4f6;
  margin-bottom: 8px;
  opacity: 0.93;
  font-family: 'Inter', 'Segoe UI', Arial, sans-serif;
}

.modern-fee-summary-value {
  font-size: 1.4rem;
  font-weight: 900;
  letter-spacing: 0.5px;
  color: #ffffff;
  line-height: 1.1;
  text-shadow: 0 2px 8px rgba(60, 72, 100, 0.10);
  font-family: 'Inter', 'Segoe UI', Arial, sans-serif;
}

.modern-fee-summary-glow {
  position: absolute;
  right: -40px;
  bottom: -40px;
  width: 120px;
  height: 120px;
  background: radial-gradient(circle, rgba(255, 255, 255, 0.18) 0%, rgba(255, 255, 255, 0) 80%);
  z-index: 0;
  pointer-events: none;
  filter: blur(2px);
}

@media (max-width: 900px) {
  .modern-fee-summary-grid {
    grid-template-columns: 1fr;
    gap: 20px;
    padding: 10px 0 0 0;
  }

  .modern-fee-summary-card {
    padding: 28px 16px 24px 16px;
    min-height: 120px;
  }

  .modern-fee-summary-value {
    font-size: 1.5rem;
  }
}
</style>