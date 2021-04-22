<template>
  <div class="card" id="f-edit-create">
    <div class="card-header">{{ title }}</div>
    <div class="card-body">
      <form id="form-main">
        <div class="form-group">
          <label for="exampleInputEmail1">Tiêu đề</label>
          <input
            type="text"
            class="form-control"
            placeholder="Enter title"
            v-model="post.title"
          />
        </div>
        <div class="form-group">
          <label for="exampleInputPassword1">Mô tả ngắn</label>
          <input
            type="text"
            class="form-control"
            placeholder="Mô tả ngắn"
            v-model="post.des"
          />
        </div>
        <div class="form-group">
          <label for="exampleFormControlTextarea1">Chi tiết</label>
          <textarea
            class="form-control"
            rows="3"
            v-model="post.detail"
          ></textarea>
        </div>
        <div class="form-group">
          <label for="exampleFormControlTextarea1">Hình ảnh</label>
          <div>
            <input type="file" class="mb-1" />
          </div>
          <img :src="image" alt="" v-if="edit" />
        </div>
        <div class="form-group">
          <label for="exampleFormControlTextarea1">Loại</label>
          <div>
            <select v-model="post.category">
              <option value="" disabled>Chọn loại</option>
              <option
                v-for="item in constantSystem.CATEGORIES"
                :key="item.id"
                :value="item.id"
              >
                {{ item.name }}
              </option>
            </select>
          </div>
        </div>
        <div class="form-group">
          <label for="exampleFormControlTextarea1">Vị trí</label>
          <div v-for="item in constantSystem.POSITIONS" :key="item.id">
            <input
              type="checkbox"
              v-model="post.position"
              name="position"
              :value="item.id"
            />
            <label for="jack">{{ item.name }}</label>
          </div>
        </div>
        <div class="form-group">
          <label for="exampleFormControlTextarea1">Public</label>
          <div>
            <input
              type="radio"
              name="public"
              value="true"
              v-model="post.public"
            />
            Yes
          </div>
          <div>
            <input
              type="radio"
              name="public"
              value="false"
              v-model="post.public"
            />
            No
          </div>
        </div>
        <div class="form-group">
          <label for="exampleFormControlTextarea1">Date Public</label>
          <div>
            <input type="date" name="" v-model="post.data_pubblic" />
          </div>
        </div>
        <div class="form-group d-flex justify-content-end mt-5">
          <div class="w-75">
            <button
              type="button"
              class="btn btn-primary mr-3 btn-submit"
              @click="submitData"
            >
              Submit
            </button>
            <button type="button" class="btn btn-primary" @click="clearForm()">
              Clear
            </button>
          </div>
        </div>
      </form>
    </div>
  </div>
</template>
<script>
import constantSystem from "../../constant/constantSystem.vue";
export default {
  data() {
    return {
      image: "",
      constantSystem: constantSystem,
    };
  },
  props: ["post", "title", "edit"],
  methods: {
    removeImage: function () {
      this.image = "";
    },
    async updateBlog(post) {
      var url = this.constantSystem.BASE_API + this.post.id;
      const response = await this.$axios.$put(url, post);
    },
    async createBlog(post) {
      const response = await this.$axios.$post(
        this.constantSystem.BASE_API,
        post
      );
    },
    submitData: function () {
      var positions = new Array(this.post.position);
      positions = positions[0].map(function (item) {
        return parseInt(item);
      });
      var post = {
        title: this.post.title,
        des: this.post.des,
        detail: this.post.detail,
        image: this.post.image,
        category: this.post.category,
        position: positions,
        public: this.post.public,
        data_pubblic: this.post.data_pubblic,
      };
      if (this.edit) {
        this.updateBlog(post);
      } else {
        post.id = Math.floor(Math.random() * (10000 - 77)) + 77;
        post.image = "https://picsum.photos/200/300";
        this.createBlog(post);
      }
    },
    clearForm() {
      this.post = {
        title: "",
        des: "",
        detail: "",
        image: "",
        category: "",
        position: [],
        public: true,
        data_pubblic: "",
      };
    },
  },
  updated() {
    this.image = this.post.thumbs;
  },
};
</script>
<style>
#f-edit-create {
  padding: 0;
  border: none;
}
#f-edit-create .card-header {
  padding-left: 0;
  background: none;
  border: none;
  font-weight: bold;
  font-size: 1.3rem;
}
.btn-submit {
  background: #2ba847;
}
</style>
