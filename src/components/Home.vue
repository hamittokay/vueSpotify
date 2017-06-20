 <template>
  <div>
    <h1>Need Music?</h1>
    <p class="lead">This is a spotify app.Just type artist and get more..</p>
    <div class="form-group">
      <input type="text"
             @keyup="callback()"
             v-model="searchStr"
             placeholder="Type artist..."
             class="form-control">
    </div>
    <ul>
      <li class="well"
          v-for="artist in artists">
        <user-item :user="artist"></user-item>
      </li>
    </ul>
  </div>
</template>

<script>
import UserItem from './UserItem.vue'

export default {
  name: 'Home',
  data() {
    return {
      searchStr: null,
      artists: {}
    }
  },
  methods: {
    callback() {
      fetch(`https://api.spotify.com/v1/search?q=${this.searchStr}&type=artist`)
        .then((res) => { return res.json() })
        .then((res) => { return this.artists = res.artists.items })
    }
  },
  components: { UserItem }
}
</script>


<style scoped>
li {
  display: block;
}

li:after {
  content: '';
  display: block;
  clear: both
}
</style>
