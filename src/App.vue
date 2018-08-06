<template>
  <div>
    <b-card no-body>
      <b-tabs card>
        <!-- Render Tabs -->


        <b-tab :title="`Tab ${i}`" v-for="i in tabs" :key="i">
           <div>

            <b-embed type="iframe"
                     aspect="21by9"
                     src="tube.html"
                     allowfullscreen
            ></b-embed>
          </div>

          <b-btn size="sm" variant="danger" class="float-right" @click="()=>closeTab(i)">
            Close tab
          </b-btn>
        </b-tab>

        <!-- New Tab Button (Using tabs slot) -->
        <b-nav-item slot="tabs" @click.prevent="newTab" href="#">
          +
        </b-nav-item>



        <!-- Render this if no tabs -->
        <div slot="empty" class="text-center text-muted">
          Currently there are no open tabs.
          <br> Open a new tab using the + button.
        </div>
      </b-tabs>
    </b-card>

  </div>
</template>

<script>
    export default {
        data () {
            return {
                tabs: [],
                tabCounter: 0
            }
        },
        methods: {
            closeTab (x) {
                for (let i = 0; i < this.tabs.length; i++) {
                    if (this.tabs[i] === x) {
                        this.tabs.splice(i, 1)
                    }
                }
            },
            newTab () {
                this.tabs.push(this.tabCounter++)
            }
        }
    }
</script>



<style lang="scss">
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
