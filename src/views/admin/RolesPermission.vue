<template>
  <div class="md:mt-5 mx-auto bg-white shadow-lg rounded-xl p-6">

    <div class="flex justify-between items-center mb-4">
      <h2 class="text-xl font-semibold text-gray-800">
        School Roles & Permissions
      </h2>

      <router-link
        to="/admin/rolespermission/create"
        class="px-4 py-2 bg-blue-600 text-white rounded-lg hover:bg-blue-700 transition"
      >
        Add Role
      </router-link>
    </div>

    <div v-if="roles.length === 0" class="text-gray-500 text-center py-8">
      No roles added yet.
    </div>

    <div v-else class="overflow-x-auto">
      <table class="w-full text-left">
        <thead>
          <tr class="border-b">
            <th class="px-4 py-3">Role</th>
            <th class="px-4 py-3">Permissions</th>
            <th class="px-4 py-3 text-right">Action</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="(item, index) in roles" :key="index" class="border-b hover:bg-gray-50">
            <td class="px-4 py-4 font-medium">{{ item.role }}</td>
            <td class="px-4 py-4">
              <span
                v-for="(perm, pIndex) in item.permissions"
                :key="pIndex"
                class="inline-block px-3 py-1 bg-gray-100 text-xs rounded-full mr-2 mb-2"
              >
                {{ perm }}
              </span>
            </td>
            <td class="px-4 py-4 text-right">
              <button @click="deleteRole(index)" class="text-red-600 text-sm">
                Delete
              </button>
            </td>
          </tr>
        </tbody>
      </table>
    </div>

  </div>
</template>

<script setup>
import { ref } from "vue"

const roles = rolePermissions

const deleteRole = (index) => {
  roles.value.splice(index, 1)
}
</script>
