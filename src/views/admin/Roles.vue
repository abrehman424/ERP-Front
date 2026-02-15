<template>
  <div class="md:mt-5 mx-auto bg-white shadow-lg rounded-xl p-6">
    <h2 class="text-xl font-semibold mb-4">Create School Role</h2>

    <!-- Role Selection / Custom Input -->
    <div class="mb-4">
      <label class="text-sm text-gray-600">Select Role or type custom role</label>

      <input
        v-if="newRoleName === 'Custom'"
        v-model="customRoleName"
        type="text"
        placeholder="Enter Custom Role Name"
        class="w-full mt-1 border rounded-lg px-3 py-2"
      />

      <select
        v-else
        v-model="newRoleName"
        class="w-full mt-1 border rounded-lg px-3 py-2"
      >
        <option value="">Choose Role</option>
        <option v-for="role in schoolRoleOptions" :key="role" :value="role">{{ role }}</option>
        <option value="Custom">Custom Role</option>
      </select>
    </div>

    <!-- Permissions -->
    <div
      v-if="(newRoleName && newRoleName !== 'Custom') || (newRoleName === 'Custom' && customRoleName.trim().length > 0)"
      class="mb-4 max-h-60 overflow-y-auto"
    >
      <label class="text-sm text-gray-600 block mb-2">Permissions</label>

      <div class="grid grid-cols-2 gap-2">
        <label v-for="perm in allPermissions" :key="perm" class="flex items-center gap-2 text-sm">
          <input type="checkbox" :value="perm" v-model="selectedPermissions" />
          {{ perm }}
        </label>
      </div>
    </div>

    <div class="flex justify-end gap-2">
      <router-link to="/roles" class="px-3 py-2 text-gray-600">Cancel</router-link>
      <button @click="addRole" class="px-4 py-2 bg-blue-600 text-white rounded-lg">Save Role</button>
    </div>
  </div>
</template>

<script setup>
import { ref, watch } from "vue"

/* ------------------ Permissions ------------------ */
const allPermissions = [
  "Dashboard Access",
  "Manage Students",
  "Manage Teachers",
  "Manage Classes",
  "Manage Sections",
  "Manage Subjects",
  "Attendance Management",
  "Fee Management",
  "Exam Management",
  "Result Management",
  "Library Management",
  "Event Management",
  "Reports",
  "Messaging",
  "Settings Access",
]

const predefinedRoles = {
  "Super Admin": [...allPermissions],
  Principal: ["Dashboard Access","Manage Teachers","Manage Students","Exam Management","Reports","Event Management"],
  "Vice Principal": ["Dashboard Access","Manage Teachers","Manage Students","Attendance Management","Exam Management"],
  Accountant: ["Dashboard Access","Fee Management","Reports"],
  Teacher: ["Dashboard Access","Attendance Management","Exam Management","Result Management"],
  Student: ["Dashboard Access"],
  Librarian: ["Dashboard Access","Library Management"],
}

const defaultCustomPermissions = ["Dashboard Access"]

/* ------------------ State ------------------ */
const newRoleName = ref("")
const customRoleName = ref("")
const selectedPermissions = ref([])

const schoolRoleOptions = Object.keys(predefinedRoles)

/* ------------------ Watch ------------------ */
watch(newRoleName, (value) => {
  if (!value) {
    selectedPermissions.value = []
    customRoleName.value = ""
    return
  }
  if (value === "Custom") {
    selectedPermissions.value = []
  } else {
    selectedPermissions.value = [...predefinedRoles[value]]
  }
})

watch(customRoleName, (value) => {
  if (value.trim().length > 0 && selectedPermissions.value.length === 0) {
    selectedPermissions.value = [...defaultCustomPermissions]
  } else if (value.trim().length === 0) {
    selectedPermissions.value = []
  }
})

/* ------------------ Functions ------------------ */
const addRole = () => {
  let finalRoleName = newRoleName.value
  if (!finalRoleName) { alert("Please select a role"); return }

  if (finalRoleName === "Custom") {
    if (!customRoleName.value.trim()) { alert("Enter custom role name"); return }
    finalRoleName = customRoleName.value.trim()
  }

  rolePermissions.value.push({ role: finalRoleName, permissions: [...selectedPermissions.value] })

  // Reset
  newRoleName.value = ""
  customRoleName.value = ""
  selectedPermissions.value = []
}
</script>
