<template>
  <div id="app" class="flex container h-screen w-full">
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
      <div>
        <button class="flex items-center">
          <img src="" alt="" class="w-12 h-12 rounded-full border border-[#E1E8ED]"/>
          <div class="ml-4">
            <p class="text-sm font-bold">Asadbek</p>
            <p class="text-sm">@a.nosirjonov</p>
          </div>
          <i class="fas fa-angle-down ml-auto text-lg"></i>
        </button>
      </div>
    </div>
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
    }
  },
}
</script>
