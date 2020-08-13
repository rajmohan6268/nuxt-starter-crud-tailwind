<template>
  <div class="flex flex-wrap -mx-4 -mb-4 md:mb-0">
    <div class="w-full md:w-1/2 px-4 mb-4 md:mb-0">
      <div v-if="!currentPost" class="col-md-8">
        <div class="submit-form">
          <div v-if="!submitted">
            <h1 class>Add new post</h1>
            <div class="form-group">
              <label for="title">title</label>
              <input
                id="post.title"
                v-model="post.title"
                type="text"
                class="form-control"
                required
                name="title"
                placeholder="Enter Title here"
              />
            </div>

            <div class>
              <label for="body">body</label>
              <input
                id="body"
                v-model="post.body"
                class="form-control"
                required
                name="tender_refno"
                placeholder="Enter post body here"
              />
            </div>

            <div class="form-group">
              <label for="userId">user id</label>
              <input
                id="userId"
                v-model="post.userId"
                class="form-control"
                required
                name="userId"
                placeholder="Enter userId"
              />
            </div>

            <button class="btn btn-success" @click="savePost">Submit</button>
          </div>

          <div v-else>
            <h4>You submitted successfully!</h4>
            <button class="btn btn-success" @click="newPost">Add</button>
          </div>
        </div>
      </div>
      <div class="row-md-6">
        <div v-if="currentPost">
          <h3>
            <b>total posts : {{ posts.length }}</b>
          </h3>
        </div>
        <div class="input-group mb-3">
          <input v-model="title" type="text" class="form-control" placeholder="Search by Title" />
          <div class="input-group-append">
            <button class="btn btn-outline-secondary" type="button" @click="searchTitle">Search</button>
          </div>
        </div>
        <h4>
          <b>post List</b>
        </h4>
        <ul class="list-group">
          <li
            v-for="(post, index) in posts"
            :key="index"
            class="list-group-item"
            :class="{ active: index == currentIndex }"
            @click="setActivePost(post, index)"
          >{{ post.title }}</li>
        </ul>

        <button class="m-3 btn btn-sm btn-danger" @click="removeAllposts()">Remove All</button>
      </div>
      <div class="col-md-6">
        <div v-if="currentPost" class="edit-form">
          <h4>
            <b>Post detail</b>
          </h4>
          <form>
            <div class="form-group">
              <label for="title">
                <B>post title</B>
              </label>
              <input id="title" v-model="currentPost.title" type="text" class="form-control" />
            </div>

            <div class="form-group">
              <label for="body">
                <B>post body</B>
              </label>
              <input id="body" v-model="currentPost.body" class="form-control" />
            </div>

            <div class="form-group">
              <label for="userId">user id</label>
              <input id="userId" v-model="currentPost.userId" class="form-control" />
            </div>
          </form>

          <button class="badge badge-danger mr-2" @click="deletePost">Delete</button>

          <button type="submit" class="badge badge-success" @click="updatePost">Update</button>
          <p>{{ message }}</p>
        </div>

        <div v-else>
          <br />
          <p>
            <B>Please click on a Post...</B>
          </p>
        </div>
      </div>
    </div>
    <div class="w-full md:w-1/2 px-4 mb-4 md:mb-0">
      <div class="flex flex-wrap">
        <div v-for="post in posts" :key="post.id" class="w-full md:w-1/2 xl:w-1/3 p-3">
          <div class="bg-blue-100 rounded-lg shadow-lg p-5">
            <div class="flex flex-row items-center">
              <div class="flex-1 text-right md:text-center">
                <p class="font-bold text-blue-500">post:{{ post.id }}</p>
                <h5 class="font-bold uppercase text-gray-600">
                  <span class="font-extrabold text-xl flex-inline uppercase text-blue-600">Title :</span>
                  {{ post.title }}
                </h5>
                <h3 class="font-bold text-2xl">
                  <span
                    class="font-extrabold text-xl flex-inline uppercase text-purple-600"
                  >post body :</span>
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
    </div>
  </div>
</template>
<script>
import PostDataService from "../services/PostDataService";
export default {
  asyncData() {
    return {
      post: {
        id: "",
        title: "",
        body: "",
        userId: "",
      },
      submitted: false,
      posts: [],
      currentPost: null,
      currentIndex: -1,
      title: "",
      // delid: 98,
      message: "",
    };
  },
  mounted() {
    // console.log("im workingh hereeee.......");
    // PostDataService.getAll()
    //   .then((response) => {
    //     this.posts = response.data;
    //     // console.log(this.posts);
    //   })
    //   .catch((e) => {
    //     console.log(e);
    //   });
    this.retrievePosts();
  },
  methods: {
    savePost() {
      const data = {
        title: this.post.title,
        body: this.post.body,
        userId: this.post.userId,
      };
      PostDataService.create(data)
        .then((Response) => {
          this.post.id = Response.data.id;
          console.log(Response.data.id);
          this.post = {};
        })
        .catch((e) => {
          console.log(e);
        });
      this.submitted = true;
    },
    getPost() {
      PostDataService.getAll()
        .then((response) => {
          this.tenders = response.data;
          console.log(response.data);
          this.posts = response.data;
        })
        .catch((e) => {
          console.log(e);
        });
    },
    updatePost() {
      PostDataService.update(this.currentPost.id, this.currentPost)
        .then((response) => {
          console.log(response.data);
          this.message = "The Tender was updated successfully!";
        })
        .catch((e) => {
          console.log(e);
        });
    },
    deletePost() {
      PostDataService.delete(this.currentPost.id)
        .then((response) => {
          console.log(response.data);
        })
        .catch((e) => {
          console.log(e);
        });
    },
    newPost() {
      this.submitted = false;
      this.post = {};
    },

    retrievePosts() {
      PostDataService.getAll()
        .then((response) => {
          this.posts = response.data;
          console.log(response.data);
        })
        .catch((e) => {
          console.log(e);
        });
    },
    refreshList() {
      this.retrievePosts();
      this.currentPost = null;
      this.currentIndex = -1;
    },

    // setActivePost(Post, index) {
    //   this.currentPost = post;
    //   this.currentIndex = index;
    // },

    setActivePost(post, index) {
      this.currentPost = post;
      this.currentIndex = index;
    },

    removeAllposts() {
      PostDataService.deleteAll()
        .then((response) => {
          console.log(response.data);
          this.refreshList();
        })
        .catch((e) => {
          console.log(e);
        });
    },
    searchTitle() {
      PostDataService.findByTitle(this.title)
        .then((response) => {
          this.posts = response.data;
          console.log(response.data);
        })
        .catch((e) => {
          console.log(e);
        });
    },
  },
};
</script>
