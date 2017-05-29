<template>
	<div>
		<nav class="navbar navbar-inverse">
		  <div class="container">
		    <div class="navbar-header">
		      <button type="button" class="navbar-toggle collapsed" data-toggle="collapse" data-target="#navbar" aria-expanded="false" aria-controls="navbar">
		        <span class="sr-only">Toggle navigation</span>
		        <span class="icon-bar"></span>
		        <span class="icon-bar"></span>
		        <span class="icon-bar"></span>
		      </button>
		      <li class="navbar-brand"><router-link to="/">vSpotify</router-link></li>
		    </div>
		    <div id="navbar" class="collapse navbar-collapse">
		      <ul class="nav navbar-nav">
		        <li><router-link to="/">Home</router-link></li>
		        <li><router-link to="/about">About</router-link></li>
		      </ul>
		    </div>
		  </div>
		</nav> 
	</div>
</template>


<script>
export default {
	name: 'Navbar'
}
</script>

<style>
*{list-style: none;margin:0;padding:0;}
</style>