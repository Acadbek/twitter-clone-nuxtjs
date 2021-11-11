<template>
  <div id="app" class="flex container h-screen w-full">

    <!-- Side nav -->
    <div
      class="
        w-1/5
        border-r border-lighter
        px-8
        py-2
        flex flex-col
        justify-between
      "
    >
      <div>
        <!-- logo -->
        <button
          class="h-12 w-12 hover:bg-[#EFF9FF] text-3x1 rounded-full text-blue"
        >
          <i class="fab fa-instagram">logo</i>
        </button>
        <!-- /logo -->
        <!-- Menus -->
        <div>
          <button
            v-for="tab in tabs"
            :key="tab"
            @click="id = tab.id"
            :class="`flex
            items-center
            py-2
            px-4
            hover:bg-[#EFF9FF]
            rounded-full
            mr-auto
            hover:text-[#1DA1F2]
            mb-3
            focus:outline-none ${id === tab.id ? 'text-[#1DA1F2]' : ''}`"
          >
            <i :class="`${tab.icon} text-2xl mr-4 text-left`"></i>
            <p class="text-lg font-semibold text-left">{{ tab.title }}</p>
          </button>
        </div>
        <!-- /Menus -->
        <!-- Tweet btn -->
        <div
          class="
            text-white
            bg-[#1DA1F2]
            rounded-full
            font-semibold
            focus:outline-none
            w-full
            p-3
            hover:bg-[#2795D9]
            text-center
            cursor-pointer
          "
        >
          Tweet
        </div>
        <!-- /Tweet btn -->
      </div>
      <div class="w-full relative">
        <button @click="dropdown = true" class="flex items-center w-full hover:bg-[#EFF9FF] rounded-full p-2 focus:outline-none">
          <img src="../static/img/profile.png" alt="" class="w-10 h-10 rounded-full border border-[#E1E8ED] object-cover"/>
          <div class="ml-4">
            <p class="text-sm font-bold leading-tight">Asadbek</p>
            <p class="text-sm leading-tight">@a.nosirjonov</p>
          </div>
          <i class="fas fa-angle-down ml-auto text-lg"></i>
        </button>
        <div v-if="dropdown === true" class="absolute bottom-0 left-0 w-64 rounded-lg shadow-md border-[#F5F8FA] bg-white mb-16">
          <button @click="dropdown = false" class="flex items-center w-full hover:bg-[#F5F8FA] p-3 focus:outline-none">
            <img src="../static/img/profile.png" alt="" class="w-10 h-10 rounded-full border border-[#E1E8ED] object-cover"/>
            <div class="ml-4">
              <p class="text-sm font-bold leading-tight">Asadbek</p>
              <p class="text-sm leading-tight">@a.nosirjonov</p>
            </div>
            <i class="fas fa-check ml-auto text-[#1DA1F2]"></i>
          </button>
          <button @click="dropdown = false" class="w-full text-left hover:bg-[#F5F8FA] border-t border-[#E1E8ED] p-3 text-sm focus:outline-none">
            Add an existing account
          </button>
           <button @click="dropdown = false" class="w-full text-left hover:bg-[#F5F8FA] border-t border-[#E1E8ED] p-3 text-sm focus:outline-none">
            Log out @a.nosirjonov
          </button>
        </div>
      </div>
    </div>
    <!-- /Side nav -->
  </div>
</template>
<script>
export default {
  data() {
    return {
      tabs: [
        { icon: 'fas fa-home', title: 'Home', id: 'home' },
        { icon: 'fas fa-hashtag', title: 'Explore', id: 'explore' },
        { icon: 'far fa-bell', title: 'Notifications', id: 'notifications' },
        { icon: 'far fa-envelope', title: 'Messages', id: 'messages' },
        { icon: 'far fa-bookmark', title: 'Bookmark', id: 'bookmark' },
        { icon: 'fas fa-clipboard-list', title: 'Lists', id: 'lists' },
      ],
      id: 'home',
      dropdown: false
    }
  },
}
</script>
