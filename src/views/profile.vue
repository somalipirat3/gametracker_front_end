<template>
  <div class="page" v-if="profile.profile">
    <div class="banner_full_bg" :style="{ backgroundImage: 'url(' + profile.profile.avatar_url + ')' }">
    </div>
    <div class="info_box">
        <div class="container">
            <div class="row">
                <div class="col">
                    <div class="avatar_placeholder" :style="{ backgroundImage: 'url(' + profile.profile.avatar_url + ')' }"></div>
                    <h1 class="profile_username">
                        {{ profile.profile.username }}
                    </h1>
                    <span class="badge badge-round-pill bg-primary">
                        {{ profile.profile.platform }}
                    </span>
                </div>
                <div class="col txt-left">
                    world
                </div>
            </div>
        </div>
    </div>

    <div class="legends">
        Legends

        <div class="legend" v-for="legend in profile.profile.legends_played" 
        v-bind:key="legend.name"
        >
            <div v-if="legend.stats.length > 0">
                {{ legend.name }}
                <div class="legend_stats" v-for="stat in legend.stats" v-bind:key="stat.identifier">
                    {{stat.displayName }}
                    {{ stat.displayValue }}
                </div>
            </div>
        </div>
    </div>

  </div>
</template>
<script>
export default {
    name: 'Search',
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
            let platform = this.$route.params.platform
            let username = this.$route.params.username
            fetch(`http://localhost:3000/api/v1/apexlegends/profiles/${platform}/${username}`)
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