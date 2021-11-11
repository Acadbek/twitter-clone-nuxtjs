<template>
  <div id="app" class="flex container h-screen w-full">
    <!-- Side nav -->
    <div
      class="
        lg:w-1/5
        border-r border-lighter
        lpx-2
        lg:px-6
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
            <i :class="`${tab.icon} text-2xl mr-4 text-left`">.</i>
            <p class="text-lg font-semibold text-left hidden lg:block">
              {{ tab.title }}
            </p>
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
            w-12
            h-12
            lg:h-auto lg:w-full
            p-3
            hover:bg-[#2795D9]
            text-center
            cursor-pointer
          "
        >
          <p class="hidden lg:block">Tweet</p>
          <i class="fas fa-plus lg:hidden">+</i>
        </div>
        <!-- /Tweet btn -->
      </div>
      <!-- User account -->
      <div class="lg:w-full relative">
        <button
          @click="dropdown = true"
          class="
            flex
            items-center
            w-full
            hover:bg-[#EFF9FF]
            rounded-full
            p-2
            focus:outline-none
          "
        >
          <img
            src="../static/img/profile.png"
            alt=""
            class="w-10 h-10 rounded-full border border-[#E1E8ED] object-cover"
          />
          <div class="hidden lg:block ml-4">
            <p class="text-sm font-bold leading-tight">Asadbek</p>
            <p class="text-sm leading-tight">@a.nosirjonov</p>
          </div>
          <i class="fas fa-angle-down ml-auto text-lg hidden lg:block"></i>
        </button>
        <div
          v-if="dropdown === true"
          class="
            absolute
            bottom-0
            left-0
            w-64
            rounded-lg
            shadow-md
            border-[#F5F8FA]
            bg-white
            mb-16
          "
        >
          <button
            @click="dropdown = false"
            class="
              flex
              items-center
              w-full
              hover:bg-[#F5F8FA]
              p-3
              focus:outline-none
            "
          >
            <img
              src="../static/img/profile.png"
              alt=""
              class="
                w-10
                h-10
                rounded-full
                border border-[#E1E8ED]
                object-cover
              "
            />
            <div class="ml-4">
              <p class="text-sm font-bold leading-tight">Asadbek</p>
              <p class="text-sm leading-tight">@a.nosirjonov</p>
            </div>
            <i class="fas fa-check ml-auto text-[#1DA1F2]"></i>
          </button>
          <button
            @click="dropdown = false"
            class="
              w-full
              text-left
              hover:bg-[#F5F8FA]
              border-t border-[#E1E8ED]
              p-3
              text-sm
              focus:outline-none
            "
          >
            Add an existing account
          </button>
          <button
            @click="dropdown = false"
            class="
              w-full
              text-left
              hover:bg-[#F5F8FA]
              border-t border-[#E1E8ED]
              p-3
              text-sm
              focus:outline-none
            "
          >
            Log out @a.nosirjonov
          </button>
        </div>
      </div>
      <!-- /User account -->
    </div>
    <!-- /Side nav -->
    <!-- Tweets -->
    <div class="w-1/2 h-full"></div>
    <!-- /Tweets -->
    <!-- Trending -->
    <div
      class="
        w-1/3
        h-full
        border-l border-[#E1E8ED]
        py-2
        px-6
        overflow-y-scroll
        relative
      "
    >
      <input
        class="pl-12 rounded-full w-full p-2 bg-[#E1E8ED] text-sm mb-4"
        placeholder="Search Twitter"
      />
      <i
        class="
          fas
          fa-search
          absolute
          left-0
          top-0
          mt-5
          ml-12
          text-sm text-[#AAB8C2]
        "
      ></i>
      <div class="w-full rounded-lg bg-[#F5F8FA]">
        <div class="flex items-center justify-between p-3">
          <p class="text-lg font-bold">Trends for You</p>
          <i class="fas fa-cog text-lg text-blue"></i>
        </div>
        <button
          v-for="trend in trending"
          :key="trend"
          class="
            w-full
            flex
            justify-between
            hover:bg-[#E1E8ED]
            p-3
            border-t border-[#E1E8ED]
          "
        >
          <div>
            <p class="text-sm text-left leading-tight text-[#657786]">
              {{ trend.top }}
            </p>
            <p class="text-bold text-left leading-tight">{{ trend.title }}</p>
            <p class="text-left leading-tight text-[#657786]">
              {{ trend.bottom }}
            </p>
          </div>
          <i class="fas fa-angle-down text-lg text-[#657786]"></i>
        </button>
        <button
          class="
            p-3
            w-full
            hover:bg-[#E1E8ED]
            text-left text-[#1DA1F2]
            border-t border-[#E1E8ED]
          "
        >
          Show more
        </button>
      </div>
      <div class="w-full rounded-lg bg-[#F5F8FA]">
        <div class="p-3">
          <p class="text-lg font-bold">Who to Follow</p>
        </div>
        <button
          class="
            w-full
            flex
            hover:bg-[#E1E8ED]
            p-3
            border-t border-[#E1E8ED]
          "
        >
          <img
            src="../static/img/profile.png"
            alt=""
            class="w-10 h-10 rounded-full border border-[#E1E8ED] object-cover"
          />
          <div class="hidden lg:block ml-4">
            <p class="text-sm font-bold leading-tight">Asadbek</p>
            <p class="text-sm leading-tight">@a.nosirjonov</p>
          </div>
            <button class="text-sm text-[#1DA1F2]">

            </button>
        </button>
        <button
          class="
            p-3
            w-full
            hover:bg-[#E1E8ED]
            text-left text-[#1DA1F2]
            border-t border-[#E1E8ED]
          "
        >
          Show more
        </button>
      </div>
    </div>
    <!-- /Trending -->
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
      dropdown: false,
      trending: [
        {
          top: 'Trending in TX',
          title: 'Gigi',
          bottom: 'Trending with Rip Gigi',
        },
        { top: 'Music', title: 'We won', bottom: '135k Tweets' },
        { top: 'Pop', title: 'Blue Ivy', bottom: '40k Tweets' },
        { top: 'Trending in US', title: 'Denim day', bottom: '40k Tweets' },
        { top: 'Trending', title: 'When Beyonce', bottom: '25.4k Tweets' },
      ],
    }
  },
}
</script>
