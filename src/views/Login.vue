
<template>
  <div class="container">
    <h1>Login Page to KFGALLL41</h1>
    <br />
    <br />
    <div class="row">
      <div class="col-md-3">Left</div>
      <div class="col-md-6">
        <form>
          <div class="form-group">
            <input
              type="email"
              class="form-control"
              id="exampleInputEmail1"
              aria-describedby="emailHelp"
              placeholder="Enter email"
            />
          </div>
          <div class="form-group">
            <input
              type="password"
              class="form-control"
              id="exampleInputPassword1"
              placeholder="Password"
            />
          </div>
          <div class="form-check">
            <input
              type="checkbox"
              class="form-check-input"
              id="exampleCheck1"
            />
            <label class="form-check-label" for="exampleCheck1"
              >Check me out</label
            >
          </div>
          <button type="submit" class="btn btn-primary">Login</button>
        </form>
      </div>
      <div class="col-md-3">Right</div>
    </div>
  </div>
</template> 
 
<script>
export default {};
</script>

<style scoped>
</style>