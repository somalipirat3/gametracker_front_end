<template>
  <div class="page" v-if="profile">
    <div class="banner_full_bg" :style="{ backgroundImage: 'url(' + profile + ')' }">
    </div>
    <div class="info_box">
        <div class="container">
            <div class="row">
                <div class="col">
                    <div class="avatar_placeholder" :style="{ backgroundImage: 'url(' + profile + ')' }"></div>
                    <h1 class="profile_username">
                        {{ profile.player.username }}
                    </h1>
                    <span class="badge badge-round-pill bg-primary">
                        {{ profile.player.platform }}
                    </span>
                </div>
                <div class="col txt-left">
                    ...
                </div>
            </div>
        </div>
    </div>

    <div class="legends container">
        Legends
        <hr>

        <div class="legend" v-for="legend in profile.stats" 
        v-bind:key="legend.legendName"
        >
            <div v-if="legend.stat.length > 0" class="container">
                <h3>{{ legend.legendName }}</h3>
                <div class="legend_stats" v-for="stat in legend.stat" v-bind:key="stat.identifier">
                    {{stat.displayName }}
                    {{ stat.displayValue }}
                    <hr>
                </div>
            </div>
        </div>
    </div>

  </div>
</template>
<script>
export default {
    name: 'Profile',
    data ()  {
        return {
            profile: {}
        }
    },
    created () {
        this.get_data()
    },
    methods: {
        get_data () {
            fetch(`https://game-tracker-rails-fd3eq.ondigitalocean.app/v1/games/apexlegends/search/${this.$route.params.platform}/${this.$route.params.username}`)
            .then( (response) => {
                return response.json()
            })
            .then( (response) => {
                this.profile = response
                console.log(response)
            })
        }
    }
}
</script>
<style  scoped>
.banner_full_bg {
    width: 100%;
    height: 200px;
    background-position: center;
    background-size: cover;
    margin-top: -9px;
}

.info_box {
    background-color: #303038;
    width: 100%;
    padding: 12px;
}

.txt-left {
    text-align: right;
}

h1.profile_username {
    font-weight: 600;
    text-transform: capitalize;
    font-size: 1.2rem;
    padding: 0;
    margin: 0;
}

.avatar_placeholder {
    width: 90px;
    height: 90px;
    margin-top: -23px;
    background-color: #272730;
    float: left;
    margin-right: 30px;
    border-radius: 50%;
    border: 3px solid #303038;
    background-position: center;
    background-repeat: no-repeat;
    background-size: cover;
}

</style>