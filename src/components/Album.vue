<template>
	<div class="col-md-3 col-xs-12">
		<div class="album">
			<a target="_blank" :href="item.external_urls.spotify">
				<img class="album-image" :src=item.images[0].url alt="">
				<h4>{{item.name}} </h4>
			</a>
			<ul class="artists">
				<li v-for="name in item.artists">
					<span class="lead small">{{name.name}} </span>
				</li>
			</ul>
		</div>
	</div>
</template>

<script>
export default {
	name: 'Album',
	data(){
		return {

		}
	},
	props:{
		item: { required: true, type: Object }
	}
}
</script>

<style>
.album-image{
	width: 100%;
	margin-top: 30px;
}
.album {
	height: 400px;
	overflow: hidden
}
</style>