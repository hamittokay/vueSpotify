<template>
	<div>
		<template>
			<div class="col-md-2 col-xs-4">
				<img class="thumb-image"
				     :src=info.images[0].url
				     alt="">
			</div>
			<div class="col-md-10 col-xs-8">
				<h2>{{info.name}} </h2>
				<ul class="genres"
				    v-if="info.genres.length > 0">
					<span>
						<b>GENRES:</b>
					</span>
					<li class="genres"
					    v-for="genre in info.genres">
						{{genre}}
					</li>
				</ul>
				<div>
					<a target="_blank"
					   :href="info.external_urls.spotify"
					   class="link green">Go to Artist's Spotify Profile</a>
					<a @click="showAlbums()"
					   class="link">Show {{info.name}}'s albums</a>
				</div>
			</div>
		</template>
		<div class="col-md-12 albums">
			<template v-for="album in albums">
				<album :item="album"></album>
			</template>
		</div>
	</div>
</template>

<script>
import Album from './Album.vue'

export default {
	name: 'ArtistProfile',
	data() {
		return {
			info: {},
			albums: {}
		}
	},
	methods: {
		showAlbums() {
			fetch(`https://api.spotify.com/v1/artists/${this.$route.params.id}/albums`)
				.then((res) => { return res.json() })
				.then((albums) => { return this.albums = albums.items })
		}
	},
	created() {
		fetch(`https://api.spotify.com/v1/artists/${this.$route.params.id}`)
			.then((res) => { return res.json() })
			.then((res) => { return this.info = res })
	},
	components: { Album }
}
</script>

<style>
a.link {
	cursor: pointer;
	display: inline-block;
	padding: 15px 30px;
	background: #333;
	margin-right: 10px;
	color: #fff;
	border-radius: 40px;
	text-align: center;
}

.thumb-image {
	width: 100%;
	border-radius: 100%
}

.genres {
	display: inline-block;
}

.genres:after {
	content: ',';
	display: inline-block;
	margin-right: 3px;
}

.green {
	background: #2ebd59!important;
}

a:hover,
a:active,
a:focus {
	text-decoration: none;
}
</style>
