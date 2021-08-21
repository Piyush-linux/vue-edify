<template>
	  <div class="cen" v-if="alert.showAlert">
            <div class="notification is-link has-text-centered"> {{ alert.mssAlert }} </div>
        </div>
</template>
<script>

export default{
	name:"Alert",
	props:["alert"]

}

</script>
<style></style>