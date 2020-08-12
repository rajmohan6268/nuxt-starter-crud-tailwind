<template>
  <div class="flex flex-wrap">
    <div v-for="(post) in posts" :key="post.id" class="w-full md:w-1/2 xl:w-1/3 p-3">
      <div class="bg-blue-100 rounded-lg shadow-lg p-5">
        <div class="flex flex-row items-center">
          <div class="flex-1 text-right md:text-center">
            <p class="font-bold text-blue-500">post:{{ post.id }}</p>
            <h5 class="font-bold uppercase text-gray-600">
              <span class="font-extrabold text-xl flex-inline uppercase text-blue-600">Title :</span>
              {{ post.title }}
            </h5>
            <h3 class="font-bold text-2xl">
              <span class="font-extrabold text-xl flex-inline uppercase text-purple-600">post body :</span>
              {{ post.body }}
              <span class="text-green-500">
                <i class="fas fa-caret-up">
                  <p class="font-bold">user:{{ post.userId }}</p>
                </i>
              </span>
            </h3>
          </div>
        </div>
        <button
          class="bg-white hover:bg-gray-100 text-gray-800 font-semibold py-2 px-4 border border-gray-400 rounded shadow"
        >edit post</button>
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
