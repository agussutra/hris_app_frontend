<template>
    <!-- Sidebar -->
    <div class="hidden lg:block fixed lg:max-w-[295px] w-full overflow-y-auto h-full bg-white z-[999]" id="sidebarHRIS">
        <div class="px-6 py-[50px] gap-y-[50px] flex flex-col">
            <div class="flex items-center justify-between">
                <a href="#" id="toggleCloseSidebar" class="lg:hidden">
                    <svg class="w-6 h-6 text-dark" fill="none" stroke="currentColor" viewBox="0 0 24 24"
                        xmlns="http://www.w3.org/2000/svg">
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12">
                        </path>
                    </svg>
                </a>
            </div>
            <div class="flex flex-col gap-4">
                <div class="text-sm text-grey">Daily Use</div>
                <NuxtLink :to="{name: 'companies-id'}" class="nav-link active">
                    <img src="/assets/svgs/ic-grid.svg" alt="">
                    Overview
                </NuxtLink>
                <NuxtLink :to="{ name: 'companies-id-employees' }" class="nav-link">
                    <img src="/assets/svgs/ic-users.svg" alt="">
                    Employees
                </NuxtLink>
                <NuxtLink :to="{name: 'companies-id-teams'}" class="nav-link">
                    <img src="/assets/svgs/ic-briefcase.svg" alt="">
                    My Teams
                </NuxtLink>
                <NuxtLink :to="{name: 'companies-id-role'}" class="nav-link">
                    <img src="/assets/svgs/ic-flag.svg" alt="">
                    Roles
                </NuxtLink>
            </div>
            <div class="flex flex-col gap-4">
                <div class="text-sm text-grey">Others</div>
                <button @click="$auth.logout()" class="nav-link">
                    <img src="/assets/svgs/ic-signout.svg" alt="">
                    Logout
                </button>
            </div>
        </div>
    </div>
  </template>