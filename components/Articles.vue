<template>
  <div>
    <div v-for="(article, index) in articles" :key="index">
      <div style="overflow: hidden">
        <div>
          <div class="images"
               v-bind:style="{backgroundImage: 'url(' + article.editorsChoice.thumbnail.sources.landscape.large + ')'}"
               style="height: 1080px; position: relative">
            <div class="bottom">
              <nuxt-link :to="`https://www.postimees.ee/${article.id}`"
                         style="text-decoration: none;  font-size: 100px; color: white; font-family: SansSerif">
                {{ article.editorsChoice.thumbnail.title.en }}
              </nuxt-link>
            </div>
          </div>
          <div v-if="index%2!==0">
            <div class="row" style="height: 346px">
              <div style="width: 650px; background: #00a4e4">
                <div class="numberContainer">
                  <div style="margin: auto; text-align: center; padding-top: 60px">
                    {{ index + 1 }}
                  </div>
                </div>
              </div>
              <div class="col" style="background: black;">
                <div v-html="article.articleLead[0].html"
                     style="color: white; font-size: 30px; line-height: 48px; padding-top: 65px; padding-bottom: 65px; padding-left: 225px; padding-right: 225px; font-family: SansSerif">
                </div>
              </div>
            </div>
          </div>
          <div v-else>
            <div class="row" style="height: 346px">
              <div class="col" style="background: #171718;">
                <div v-html="article.articleLead[0].html"
                     style="color: white; font-size: 30px; line-height: 48px; padding-top: 65px; padding-bottom: 65px; padding-left: 225px; padding-right: 225px; font-family: SansSerif">
                </div>
              </div>
              <div style="width: 650px; background: #00a4e4">
                <div class="numberContainer">
                  <div style="margin: auto; text-align: center; padding-top: 60px">
                    {{ index + 1 }}
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      articles: []
    }
  },
  async fetch() {
    this.articles = await fetch(
      'https://services.postimees.ee/rest/v1/sections/81/editorsChoice/articles?limit=5'
    ).then(res => res.json())
  }
}
</script>
<style>
.images {
  background-image: -moz-linear-gradient(0deg, rgb(0, 0, 0) 0%, rgba(0, 0, 0, 0.18039) 100%);
  background-image: -webkit-linear-gradient(0deg, rgb(0, 0, 0) 0%, rgba(0, 0, 0, 0.18039) 100%);
  background-image: -ms-linear-gradient(0deg, rgb(0, 0, 0) 0%, rgba(0, 0, 0, 0.18039) 100%);
}
.numberContainer {
  width: 190px;
  height: 190px;
  border-radius: 190px;
  background: none;
  border: solid white 2px;
  margin-left: auto;
  margin-right: auto;
  margin-top: 73px;
  color: white;
  font-size: 48px;
  opacity: 50%;
  font-family: SansSerif;
}
html, body {
  height: 100%;
  margin: 0;
  padding: 0;
}
.bottom {
  position: absolute;
  bottom: 0;
  left: 0;
  padding-bottom: 142px;
  margin-top: auto;
  padding-left: 130px;
}
</style>
