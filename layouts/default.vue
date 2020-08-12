
<template>
  <div class="bg-gray-900 font-sans leading-normal tracking-normal mt-12">
    <!--Nav-->
    <nav class="bg-gray-900 pt-2 md:pt-1 pb-1 px-1 mt-0 h-auto fixed w-full z-20 top-0">
      <div class="flex flex-wrap items-center">
        <div class="flex flex-shrink md:w-1/3 justify-center md:justify-start text-white">
          <a href="#">
            <span class="text-xl pl-2">
              <i class="em em-grinning"></i>
            </span>
          </a>
        </div>

        <div class="flex flex-1 md:w-1/3 justify-center md:justify-start text-white px-2">
          <span class="relative w-full">
            <input
              type="search"
              placeholder="Search"
              class="w-full bg-gray-800 text-sm text-white transition border border-transparent focus:outline-none focus:border-gray-700 rounded py-1 px-2 pl-10 appearance-none leading-normal"
            />
            <div class="absolute search-icon" style="top: .5rem; left: .8rem;">
              <svg
                class="fill-current pointer-events-none text-white w-4 h-4"
                xmlns="http://www.w3.org/2000/svg"
                viewBox="0 0 20 20"
              >
                <path
                  d="M12.9 14.32a8 8 0 1 1 1.41-1.41l5.35 5.33-1.42 1.42-5.33-5.34zM8 14A6 6 0 1 0 8 2a6 6 0 0 0 0 12z"
                />
              </svg>
            </div>
          </span>
        </div>
        <div class="flex w-full pt-2 content-center justify-between md:w-1/3 md:justify-end">
          <ul class="list-reset flex justify-between flex-1 md:flex-none items-center">
            <li class="flex-1 md:flex-none md:mr-3">
              <a class="inline-block py-2 px-4 text-white no-underline" href="/test">test</a>
            </li>
            <li class="flex-1 md:flex-none md:mr-3">
              <a
                class="inline-block text-gray-600 no-underline hover:text-gray-200 hover:text-underline py-2 px-4"
                href="#"
              >link</a>
            </li>
            <li class="flex-1 md:flex-none md:mr-3">
              <div class="relative inline-block"></div>
            </li>
          </ul>
        </div>
      </div>
    </nav>

    <div class="flex flex-col md:flex-row">
      <div
        class="bg-gray-900 shadow-lg h-16 fixed bottom-0 mt-12 md:relative md:h-screen z-10 w-full md:w-48"
      >
        <div
          class="md:mt-12 md:w-48 md:fixed md:left-0 md:top-0 content-center md:content-start text-left justify-between"
        >
          <ul
            class="list-reset flex flex-row md:flex-col py-0 md:py-3 px-1 md:px-2 text-center md:text-left"
          >
            <li class="mr-3 flex-1">
              <a
                href="#"
                class="block py-1 md:py-3 pl-1 align-middle text-white no-underline hover:text-white border-b-2 border-gray-800 hover:border-pink-500"
              >
                <i class="fas fa-tasks pr-0 md:pr-3"></i>
                <span
                  class="pb-1 md:pb-0 text-xs md:text-base text-gray-600 md:text-gray-400 block md:inline-block"
                >Tasks</span>
              </a>
            </li>
            <li class="mr-3 flex-1">
              <a
                href="#"
                class="block py-1 md:py-3 pl-1 align-middle text-white no-underline hover:text-white border-b-2 border-gray-800 hover:border-purple-500"
              >
                <i class="fa fa-envelope pr-0 md:pr-3"></i>
                <span
                  class="pb-1 md:pb-0 text-xs md:text-base text-gray-600 md:text-gray-400 block md:inline-block"
                >crud</span>
              </a>
            </li>

            <li class="mr-3 flex-1">
              <a
                href="#"
                class="block py-1 md:py-3 pl-1 align-middle text-white no-underline hover:text-white border-b-2 border-gray-800 hover:border-purple-500"
              >
                <i class="fa fa-envelope pr-0 md:pr-3"></i>
                <span
                  class="pb-1 md:pb-0 text-xs md:text-base text-gray-600 md:text-gray-400 block md:inline-block"
                >get</span>
              </a>
            </li>
            <li class="mr-3 flex-1">
              <a
                href="#"
                class="block py-1 md:py-3 pl-1 align-middle text-white no-underline hover:text-white border-gray-800 border-b-2 hover:border-blue-600"
              >
                <i class="fas fa-chart-area pr-0 md:pr-3 text-blue-600"></i>
                <span
                  class="pb-1 md:pb-0 text-xs md:text-base text-white md:text-white block md:inline-block"
                >post</span>
              </a>
            </li>
            <li class="mr-3 flex-1">
              <a
                href="#"
                class="block py-1 md:py-3 pl-0 md:pl-1 align-middle text-white no-underline border-b-2 border-gray-800 hover:border-red-500"
              >
                <i class="fa fa-wallet pr-0 md:pr-3"></i>
                <span
                  class="pb-1 md:pb-0 text-xs md:text-base text-gray-600 md:text-gray-400 block md:inline-block"
                >put</span>
              </a>
            </li>
            <li class="mr-3 flex-1">
              <a
                href="#"
                class="block py-1 md:py-3 pl-1 align-middle text-white no-underline hover:text-white border-b-2 border-gray-800 hover:border-purple-500"
              >
                <i class="fa fa-envelope pr-0 md:pr-3"></i>
                <span
                  class="pb-1 md:pb-0 text-xs md:text-base text-gray-600 md:text-gray-400 block md:inline-block"
                >delete</span>
              </a>
            </li>
          </ul>
        </div>
      </div>

      <div class="main-content flex-1 bg-gray-100 mt-12 md:mt-2 pb-24 md:pb-5">
        <div class="bg-blue-800 p-2 shadow text-xl text-white">
          <h3 class="font-bold pl-2">Nuxt crud</h3>
        </div>
        <Nuxt />
      </div>
    </div>
  </div>
</template>
<script>
import PostDataService from "../services/PostDataService";
export default {
  asyncData() {
    return {
      post: {
        id: 0,
        title: "",
        body: "",
        userId: 0,
      },
      // submitted: false,
      posts: [],
      delid: 98,
    };
  },
  mounted() {
    console.log("im workingh hereeee.......");
    PostDataService.getAll()
      .then((response) => {
        this.posts = response.data;
        console.log(this.posts);
      })
      .catch((e) => {
        console.log(e);
      });
  },
  methods: {
    // savePost() {
    //   const data = {
    //     title: this.post.title,
    //     body: this.post.body,
    //     userId: this.post.userId,
    //   };
    //   PostDataService.create(data)
    //     .then((Response) => {
    //       this.post.id = Response.data.id;
    //       console.log(Response.data.id);
    //       this.currentPost = Response.data;
    //       console.log(this.currentPost.data);
    //       this.currentPostid = Response.data.id;
    //     })
    //     .catch((e) => {
    //       console.log(e);
    //     });
    // },
    // getPost() {
    //   PostDataService.getAll()
    //     .then((response) => {
    //       this.tenders = response.data;
    //       console.log(response.data);
    //       this.posts = response.data;
    //     })
    //     .catch((e) => {
    //       console.log(e);
    //     });
    // },
    // updatepost() {
    //   PostDataService.update(98, this.post)
    //     .then((response) => {
    //       console.log(response.data);
    //     })
    //     .catch((e) => {
    //       console.log(e);
    //     });
    // },
    // deletePost() {
    //   PostDataService.delete(this.delid)
    //     .then((response) => {
    //       console.log(response.data);
    //     })
    //     .catch((e) => {
    //       console.log(e);
    //     });
    // },
  },
};
</script>
