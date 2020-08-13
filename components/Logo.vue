<template>
 
  <div    >

 
   
 <div class="col-md-6">
   <div v-if="currentPost" class="edit-form">
      <h4><b>Post detail</b></h4>
    <form>
      <div class="form-group">
        <label for="title"><B>post title</B></label>
        <input
          type="text"
          class="form-control"
          id="title"
          v-model="currentPost.title"
        />
      </div>

      <div class="form-group">
        <label for="body"><B>post body</B></label>
        <input
          class="form-control"
          id="body"
          v-model="currentPost.body"
          
        />
      </div>

      <div class="form-group">
        <label for="userId"> user id</label>
        <input
          class="form-control"
          id="userId"
          v-model="currentPost.userId"
        />
      </div>
    </form>


    <button class="badge badge-danger mr-2"
      @click="deletePost"
    >
      Delete
    </button>

    <button type="submit" class="badge badge-success"
      @click="updatePost"
    >
      Update
    </button>
    <p>{{ message }}</p>
  </div>

  <div v-else>
    <br />
    <p><B>Please click on a Post...</B></p>
  </div>


</div>


<!-- edit sec -->
  
  </div>
</template>
