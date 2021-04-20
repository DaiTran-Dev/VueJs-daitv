<template>
  <div class="card">
    <div class="card-header">{{ title }}</div>
    <div class="card-body">
      <form>
        <div class="form-group">
          <label for="exampleInputEmail1">Tiêu đề</label>
          <input type="text" class="form-control" placeholder="Enter email" />
        </div>
        <div class="form-group">
          <label for="exampleInputPassword1">Mô tả ngắn</label>
          <input type="text" class="form-control" placeholder="Password" />
        </div>
        <div class="form-group">
          <label for="exampleFormControlTextarea1">Chi tiết</label>
          <textarea class="form-control" rows="3"></textarea>
        </div>
        <div class="form-group">
          <label for="exampleFormControlTextarea1">Hình ảnh</label>
          <br />
          <input type="file" />
        </div>
        <div class="form-group">
          <label for="exampleFormControlTextarea1">Loại</label>
          <br />
          <select>
            <option disabled value="">Please select one</option>
            <option value="thoiSu">Thời Sự</option>
            <option value="tinVan">Tin Vắn</option>
          </select>
        </div>
        <div class="form-group">
          <label for="exampleFormControlTextarea1">Vị trí</label>
          <br />
          <input type="checkbox" value="VietNam" />
          <label for="jack">VietNam</label>
          <br />
          <input type="checkbox" value="ChauA" />
          <label for="john">Châu Á</label>
          <br />
          <input type="checkbox" id="mike" value="ChauAu" />
          <label for="mike">Châu Âu</label>
          <br />
        </div>
        <div class="form-group">
          <label for="exampleFormControlTextarea1">Public</label>
          <br />
          <input type="radio" name="public" id="" value="radio" /> Yes
          <br />
          <input type="radio" name="public" id="" value="radio" /> No
        </div>
        <div class="form-group">
          <label for="exampleFormControlTextarea1">Date Public</label>
          <br />
          <input type="date" name="" />
        </div>
        <div class="form-group d-flex">
          <button type="submit" class="btn btn-primary mr-5">Submit</button>
          <button type="button" class="btn btn-primary">Clear</button>
        </div>
      </form>
    </div>
  </div>
</template>
<script>
export default {
  props: ["title"],
};
</script>
