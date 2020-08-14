<template>
  <div>
    <div class="bg-blue-800 p-2 shadow text-xl text-white">
      <div class="flex flex-1 md:w-1/3 justify-center md:justify-start text-white px-2">
        <span class="relative w-full">
          <input
            v-model="title"
            type="search"
            placeholder="Search by Title"
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
    </div>
    <div class="flex flex-wrap -mx-4 -mb-4 md:mb-0">
      <div class="w-full md:w-1/2 px-4 mb-4 md:mb-0">
        <div v-if="!currentPost" class="w-full max-w-xs">
          <form class="bg-white shadow-md rounded px-8 pt-6 pb-8 mb-4">
            <div v-if="!submitted">
              <div class="mb-4">
                <span class="font-bold text-2xl text-gray-300">Add new post</span>
                <label class="block text-gray-700 text-sm font-bold mb-2" for="title">Title</label>
                <input
                  id="post.title"
                  v-model="post.title"
                  type="text"
                  class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
                  required
                  name="title"
                  placeholder="Enter Title here"
                />
              </div>
              <div class="mb-4">
                <label class="block text-gray-700 text-sm font-bold mb-2" for="body">body</label>
                <input
                  id="body"
                  v-model="post.body"
                  class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
                  required
                  name="tender_refno"
                  placeholder="Enter post body here"
                />
              </div>
              <div class="mb-4">
                <label class="block text-gray-700 text-sm font-bold mb-2" for="userId">UserId</label>
                <input
                  id="userId"
                  v-model="post.userId"
                  class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
                  required
                  name="userId"
                  placeholder="Enter userId"
                />
              </div>
              <div class="flex items-center justify-between">
                <button
                  class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded focus:outline-none focus:shadow-outline"
                  @click="savePost"
                >Submit (create post)</button>
              </div>
            </div>
            <div v-else>
              <h4>You submitted successfully!</h4>
              <button
                class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded focus:outline-none focus:shadow-outline"
                @click="newPost"
              >Add new</button>
            </div>
          </form>
        </div>
        <!-- <div v-if="!currentPost" class="col-md-8">
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
        </div>-->
        <div class="row-md-6">
          <div v-if="currentPost">
            <h3>
              <b>total posts : {{ posts.length }}</b>
            </h3>
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

          <button
            class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded focus:outline-none focus:shadow-outline"
            @click="removeAllposts()"
          >Remove All</button>
        </div>

        <div class="col-md-6">
          <div v-if="currentPost" class="bg-white shadow-md rounded px-8 pt-6 pb-8 mb-4">
            <div class="mb-4">
              <b>Post detail</b>
            </div>
            <form>
              <div class="block text-gray-700 text-sm font-bold mb-2">
                <label for="title">
                  <B>post title</B>
                </label>
                <input
                  id="title"
                  v-model="currentPost.title"
                  type="text"
                  class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
                />
              </div>

              <div class="block text-gray-700 text-sm font-bold mb-2">
                <label for="body">
                  <B>post body</B>
                </label>
                <input
                  id="body"
                  v-model="currentPost.body"
                  class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
                />
              </div>

              <div class="block text-gray-700 text-sm font-bold mb-2">
                <label for="userId">user id</label>
                <input
                  id="userId"
                  v-model="currentPost.userId"
                  class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
                />
              </div>
              <table>
                <th>
                  <Span class="font-bold text-blue-300">post id:</Span>
                </th>

                <th class="font-bold align-baseline">{{ currentPost.id }}</th>
              </table>
            </form>

            <button
              class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded focus:outline-none focus:shadow-outline"
              @click="deletePost"
            >Delete</button>

            <button
              type="submit"
              class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded focus:outline-none focus:shadow-outline"
              @click="updatePost"
            >Update</button>
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
          <div v-for="post in posts" :key="post.id" class="w-full p-3">
            <div class="bg-blue-100 rounded-lg shadow-lg p-5">
              <div class="flex flex-row items-center">
                <div class="flex-1 text-right md:text-center">
                  <p class="font-bold text-blue-500">post:{{ post.id }}</p>
                  <h5 class="font-bold uppercase text-gray-600">
                    <span class="font-medium flex-inline uppercase text-blue-600">Title :</span>
                    {{ post.title }}
                  </h5>
                  <h3 class="font-bold text-base">
                    <span class="flex-inline uppercase text-purple-600">post body :</span>
                    {{ post.body }}
                    <span class="text-green-500">
                      <p class="font-base">user:{{ post.userId }}</p>
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
  </div>
</template>
<script>
import PostDataService from "../services/PostDataService"
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
    }
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
    this.retrievePosts()
  },
  methods: {
    savePost() {
      const data = {
        title: this.post.title,
        body: this.post.body,
        userId: this.post.userId,
      }
      PostDataService.create(data)
        .then((Response) => {
          this.post.id = Response.data.id
          this.posts.push(Response.data)
          console.log(Response.data.id)
          this.post = {}
        })
        .catch((e) => {
          console.log(e)
        })
      this.submitted = true
    },
    getPost() {
      PostDataService.getAll()
        .then((response) => {
          this.tenders = response.data
          console.log(response.data)
          this.posts = response.data
        })
        .catch((e) => {
          console.log(e)
        })
    },
    updatePost() {
      PostDataService.update(this.currentPost.id, this.currentPost)
        .then((response) => {
          console.log(response.data)
          this.message = "The Tender was updated successfully!"
        })
        .catch((e) => {
          console.log(e)
        })
    },
    deletePost() {
      PostDataService.delete(this.currentPost.id)
        .then((response) => {
          console.log(response.data)
        })
        .catch((e) => {
          console.log(e)
        })
    },
    newPost() {
      this.submitted = false
      this.post = {}
    },

    retrievePosts() {
      PostDataService.getAll()
        .then((response) => {
          this.posts = response.data
          console.log(response.data)
        })
        .catch((e) => {
          console.log(e)
        })
    },
    refreshList() {
      this.retrievePosts()
      this.currentPost = null
      this.currentIndex = -1
    },

    // setActivePost(Post, index) {
    //   this.currentPost = post
    //   this.currentIndex = index
    // },

    setActivePost(post, index) {
      this.currentPost = post
      this.currentIndex = index
    },

    removeAllposts() {
      PostDataService.deleteAll()
        .then((response) => {
          console.log(response.data)
          this.refreshList()
        })
        .catch((e) => {
          console.log(e)
        })
    },
    searchTitle() {
      PostDataService.findByTitle(this.title)
        .then((response) => {
          this.posts = response.data
          console.log(response.data)
        })
        .catch((e) => {
          console.log(e)
        })
    },
  },
}
</script>
