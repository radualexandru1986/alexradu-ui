<template>
  <div class="col-12 col-md-6">
    <div class="card mt-2">
      <div class="card-body">
        <h5 class="card-title"> {{details.created_at}}  </h5>
        <h6 class="card-subtitle mb-2 text-muted">@{{JSON.parse(details.user).screen_name}}</h6>
        <div class="row d-inline">
          <span><strong>{{JSON.parse(details.user).location}}</strong></span>
          <span><strong>{{JSON.parse(details.user).followers_count}}</strong> Followers</span>
          <span><strong>{{JSON.parse(details.user).friends_count}}</strong> Friends</span>
        </div>
        <div class="row mt-2">
          <p class="card-text"> {{details.text}} </p>
        </div>

      </div>
    </div>
  </div>
</template>

<script>
export default {
  props : {
    details : Object
  },
  name: "CardComponent"
}
</script>

<style scoped>

</style>