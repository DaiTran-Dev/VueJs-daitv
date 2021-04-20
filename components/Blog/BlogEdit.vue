<template>
  <div class="card">
    <div class="card-header">{{ title }} {{ edit }}</div>
    <div class="card-body">
      <form>
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
          <br />
          <input type="file" />
          <br />
          <img :src="image" alt="" />
          <br />
        </div>
        <div class="form-group">
          <label for="exampleFormControlTextarea1">Loại</label>
          <br />
          <select v-model="post.category">
            <option disabled value="">Please select one</option>
            <option value="0">Tin Vắn</option>
            <option value="1">Thời Sự</option>
          </select>
        </div>
        <div class="form-group">
          <label for="exampleFormControlTextarea1">Vị trí</label>
          <br />
          <input
            type="checkbox"
            v-model="post.position"
            name="position"
            value="0"
          />
          <label for="jack">VietNam</label>
          <br />
          <input
            type="checkbox"
            v-model="post.position"
            name="position"
            value="1"
          />
          <label for="john">Châu Á</label>
          <br />
          <input
            type="checkbox"
            v-model="post.position"
            name="position"
            value="2"
          />
          <label for="mike">Châu Âu</label>
          <br />
          <input
            type="checkbox"
            v-model="post.position"
            name="position"
            value="3"
          />
          <label for="mike">Châu Mỹ</label>
          <br />
        </div>
        <div class="form-group">
          <label for="exampleFormControlTextarea1">Public</label>
          <br />
          <input
            type="radio"
            name="public"
            value="true"
            v-model="post.public"
          />
          Yes
          <br />
          <input
            type="radio"
            name="public"
            value="false"
            v-model="post.public"
          />
          No
        </div>
        <div class="form-group">
          <label for="exampleFormControlTextarea1">Date Public</label>
          <br />
          <input type="date" name="" v-model="post.data_pubblic" />
        </div>
        <div class="form-group d-flex">
          <button
            type="button"
            class="btn btn-primary mr-5"
            @click="submitData"
          >
            Submit
          </button>
          <button type="button" class="btn btn-primary">Clear</button>
        </div>
      </form>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      image: "",
    };
  },
  props: ["post", "title", "edit"],
  methods: {
    removeImage: function () {
      this.image = "";
    },
    async updateBlog(data) {
      var url = "http://localhost:3000/blogs/" + this.post.id;
      const response = await this.$axios.$put(url, data);
    },
    async createBlog(data) {
      var url = "http://localhost:3000/blogs/";
      const response = await this.$axios.$post(url, data);
    },
    submitData: function () {
      var positions = new Array(this.post.position);
      var positionData = positionsF[0].map(function (value) {
        return parseInt(value);
      });
      var data = {
        title: this.post.title,
        des: this.post.des,
        detail: this.post.detail,
        image: this.post.image,
        category: this.post.category,
        position: positionData,
        public: this.post.public,
        data_pubblic: this.post.data_pubblic,
      };
      if (this.edit) {
        this.updateBlog(data);
      } else {
        data.id = Math.floor(Math.random() * (10000 - 77)) + 77;
        data.image = "https://picsum.photos/200/300";
        this.createBlog(data);
      }
    },
  },
  updated() {
    this.image = this.post.thumbs;
  },
};
</script>
