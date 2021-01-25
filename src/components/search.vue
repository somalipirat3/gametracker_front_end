<template>
<div class="row">
    <div class="col">
        <div class="search_component">
            <!-- {{ icons_styling }} -->
            <div class="searchbox">
                <input type="search" id="search_input" class="search_input" placeholder="Search ..." v-model="search_term" v-on:change="get_data()">
                <div class="labels">
                    
                    <label for="search_input" class="search-icon icon-pc" v-on:click="set_pc()" v-bind:class="{ active_pc: icons_styling.pc }">
                        <svg version="1.1" xmlns="http://www.w3.org/2000/svg" width="32" height="32" viewBox="0 0 32 32" fill="currentColor">
                            <path d="M0 2v20h32v-20h-32zM30 20h-28v-16h28v16zM21 24h-10l-1 4-2 2h16l-2-2z"></path>
                        </svg>
                    </label>
                    

                    <label for="search_input" class="search-icon icon-xbox" v-on:click="set_xbox()"  v-bind:class="{ active_xbox: icons_styling.xbox }" > 
                        <svg viewBox="0 0 88 88" class="icon platform-icon platform-xbl" fill="currentColor">
                            <path d="M39.73 86.91c-6.628-.635-13.338-3.015-19.102-6.776-4.83-3.15-5.92-4.447-5.92-7.032 0-5.193 5.71-14.29 15.48-24.658 5.547-5.89 13.275-12.79 14.11-12.604 1.626.363 14.616 13.034 19.48 19 7.69 9.43 11.224 17.154 9.428 20.597-1.365 2.617-9.837 7.733-16.06 9.698-5.13 1.62-11.867 2.306-17.416 1.775zM8.184 67.703c-4.014-6.158-6.042-12.22-7.02-20.988-.324-2.895-.21-4.55.733-10.494 1.173-7.4 5.39-15.97 10.46-21.24 2.158-2.24 2.35-2.3 4.982-1.41 3.19 1.08 6.6 3.436 11.89 8.22l3.09 2.794-1.69 2.07c-7.828 9.61-16.09 23.24-19.2 31.67-1.69 4.58-2.37 9.18-1.64 11.095.49 1.294.04.812-1.61-1.714zm70.453 1.047c.397-1.936-.105-5.49-1.28-9.076-2.545-7.765-11.054-22.21-18.867-32.032l-2.46-3.092 2.662-2.443c3.474-3.19 5.886-5.1 8.49-6.723 2.053-1.28 4.988-2.413 6.25-2.413.777 0 3.516 2.85 5.726 5.95 3.424 4.8 5.942 10.63 7.218 16.69.825 3.92.894 12.3.133 16.21-.63 3.208-1.95 7.366-3.23 10.187-.97 2.113-3.36 6.218-4.41 7.554-.54.687-.54.686-.24-.796zM40.44 11.505C36.834 9.675 31.272 7.71 28.2 7.18c-1.076-.185-2.913-.29-4.08-.23-2.536.128-2.423-.004 1.643-1.925 3.38-1.597 6.2-2.536 10.03-3.34C40.098.78 48.193.77 52.43 1.663c4.575.965 9.964 2.97 13 4.84l.904.554-2.07-.104C60.148 6.745 54.15 8.408 47.71 11.54c-1.942.946-3.63 1.7-3.754 1.68-.123-.024-1.706-.795-3.52-1.715z" data-v-6f682075=""></path>
                        </svg>
                    </label>

                    <label for="search_input" class="search-icon icon-psn" v-on:click="set_psn()"  v-bind:class="{ active_psn: icons_styling.psn }" >
                        <svg viewBox="5 117.952 990 764.096" class="icon platform-icon platform-psn" fill="currentColor">
                            <path d="M986.195 702.762c-19.338 24.398-66.718 41.803-66.718 41.803l-352.455 126.6V777.8l259.383-92.42c29.436-10.546 33.955-25.455 10.029-33.28-23.881-7.848-67.122-5.6-96.58 4.992l-172.832 60.871v-96.895l9.962-3.373s49.942-17.675 120.168-25.455c70.226-7.735 156.215 1.057 223.72 26.646 76.072 24.039 84.64 59.478 65.323 83.876zM600.572 543.781V305.019c0-28.041-5.172-53.855-31.481-61.164-20.147-6.454-32.65 12.255-32.65 40.273v597.919l-161.251-51.18V117.952c68.562 12.728 168.447 42.814 222.145 60.917 136.562 46.884 182.861 105.237 182.861 236.716-.001 128.151-79.108 176.723-179.624 128.196zM79.31 768.041c-78.096-21.992-91.093-67.82-55.497-94.22 32.898-24.375 88.845-42.725 88.845-42.725l231.208-82.211v93.725l-166.378 59.544c-29.39 10.547-33.91 25.478-10.029 33.303 23.903 7.826 67.167 5.6 96.603-4.969l79.805-28.963v83.853c-5.06.899-10.703 1.799-15.921 2.676-79.829 13.042-164.851 7.6-248.636-20.013z" data-v-6f682075=""></path>
                        </svg>
                    </label>


                </div>
            </div>

            <div class="search_term" v-if="search_term">
                {{ search_term }}
            </div>
            <div class="search_term" v-if="search_term">
                1 Result
            </div>

            <!-- <hr> -->

            <div class="profile" v-if="search_result.legend" v-on:click="show_profile()">
                <div class="row">
                    <div class="col-md-2">
                        <div class="avatar_spot" :style="{ backgroundImage: 'url(' + search_result.img_assets.avatar + ')' }" ></div>
                    </div>
                
                    <div class="information col">
                        <h3>{{ search_result.legend }}</h3>
                        <div class="row">
                            <div class="col stats" v-for="item in search_result.stats" v-bind:key="item.key">
                                <strong>{{ item.name }}</strong>
                                <h4>{{ item.value }}</h4>
                            </div>
                        </div>
                    </div>

                    
                </div>
                
            </div>

            <div class="search_result">
                <div class="result" v-for="result in search_result" v-bind:key="result.username">
                    {{ result.username }}
                    {{ result.platform }}
                    link: {{ "/player/" + result.platform + "/" + result.username}}

                    <div class="legends">
                        <ul class="legend" v-for="legend in result.stats" v-bind:key="legend.name">
                            <li>
                                {{ legend.legend }}
                            </li>
                        </ul>
                    </div>

                </div>
            </div>

        </div>
    </div>
    <div class="col-md-2">

    </div>

</div>
</template>
<script>
export default {
    name: 'Search',
    data ()  {
        return {
            search_term: '',
            icons_styling: {
                pc: false,
                xbox: false,
                psn: false,
                cached_styles: {}
            },
            search_result: {}
        }
    },
    computed: {
        platform () {
            // "origin", "psn" , "xbl"
            if (this.icons_styling.pc) {
                return "origin"
            } else if (this.icons_styling.psn) {
                return "psn"
            } else if (this.icons_styling.xbox) {
                return "xbl"
            } else {
                return ""
            }
        }
    },
    methods: {
        get_data () {
            fetch(`http://localhost:3000/api/v1/apexlegends/profiles/search/${this.platform}/${this.search_term}`)
            .then( (response) => {
                return response.json()
            })
            .then( (response) => {
                this.search_result = response['search_result']
                console.log(response)
            })
        },
        set_pc () {
            this.icons_styling = { pc: true, xbox: false, psn: false }
        },
        set_xbox () {
            this.icons_styling = { pc: false, xbox: true, psn: false }
        },
        set_psn () {
            this.icons_styling = { pc: false, xbox: false, psn: true }
        }
    }
}
</script>
<style scoped>
.search_component {
    padding: 30px;
    transition: all 0.3s ease;
}

.search_component > .searchbox {
    background-color: #303038;
    border-radius: 10px;
}
.search_component > .searchbox > .search_input {
    background-color: transparent;
    border: none;
    padding: 12px;
    width: 100%;
    padding-left: 22%;
    padding-right: 2%;
    color: white;
    font-size: 1.2rem;
    border-radius: 30px;
}


.labels {
    /* background: green; */
    width: 120px;
    position: absolute;
    margin-top: -44px;
    padding: 4px;
    text-align: center;
}

.search-icon {
    width: 40px;
    height: 40px;
    float: right;
    /* background: red; */
    cursor: pointer;
    color: white;
}
.search-icon:hover {
    color: gray;
}

.search-icon > svg {
    width: 1.3rem;
}

.icon-psn > svg {
    width: 1.7rem;
    padding-top: 5px;

}

.icon-xbox > svg {
    padding-top: 5px;
}

.searchbox .active_psn {
    color:#5666f3
}

.searchbox .active_pc {
    color:#ff6b7a
}

.searchbox .active_xbox {
    color:#50d890
}

.searchbox > input {
    outline: none;
}

.search_term {
    padding: 5px;
    border-radius: 20px;
    background: #51536B;
    display: inline-block;
    margin-top: 10px;
    margin-bottom: 10px;
    padding-left: 20px;
    padding-right: 20px;
    font-size: 0.95rem;
    margin-right: 5px;
}

.search_term:nth-child(1) {
    background-color: #303038
}

.avatar_spot {
    width: 80px;
    height: 80px;
    background-size: 169% !important;
    background-position: center;
    border-radius: 100%;
    border: 7px solid #303038;
}

.stats {
    padding: 11px;
    background: #303038;
    border-radius: 4px;
    margin: 4px;
}


@media only screen and (min-width: 600px) {
  .search_component > .searchbox {
        /* background-color: #ff6b7a; */
        border-radius: 10px;
    }

    .search_component > .searchbox > .search_input {
        padding-left: 130px;
        padding-right: 2%;
    }
}

</style>