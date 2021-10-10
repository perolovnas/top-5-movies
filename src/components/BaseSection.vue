<template>

    <section v-if="true" class="section">
      <div v-if="Index === 1" class="bg one"></div>
      <div v-if="Index === 2" class="bg two"></div>
      <div v-if="Index === 3" class="bg three"></div>
      <div v-if="Index === 4" class="bg four"></div>
      <div v-if="Index === 5" class="bg five"></div>

      <div :class="['section-inner']">

        <div class="index-wrapper">
          <h1>{{Index}}</h1>
        </div>
        <div class="image-wrapper">
          <img :src="Poster" :alt="Title">
        </div>
        <div class="meta-wrapper">
          <h3>{{Title}}</h3>
          <ul>
            <li v-for="(rating_item, i) in Ratings" :key="i">
              {{rating_item}}
            </li>
          </ul>
          <div class="plot"><p>{{Plot}}</p></div>
          <div class="actors">Known actors: {{Actors}}</div>
          <div class="director">Directed by: {{Director}}</div>
          <div class="released">Released: {{Released}}</div>
          <div class="sub-meta-wrapper">
            <div class="genre">{{Genre}}</div>
            <div class="rated">{{Rated}}</div>
            <div class="runtime">{{Runtime}}</div>
          </div>
        </div>
      </div>
    </section>

</template>

<script>
export default {
  props: {
    Title: String,
    Index: String,
    Poster: String,
    Title: String,
    Ratings: Array,
    Plot: String,
    Rated: String,
    Genre: String,
    Actors: String,
    Director: String,
    Runtime: String,
    Released: String
  }

}
</script>

<style lang="scss" scoped>
  section.section {
    position: relative;
    width: 100%;
    height: auto;
    display: flex;
    justify-content: center;
    align-items: center;
    .bg {
      position: absolute;
      z-index: -1;
      width: 100%;
      height: 100%;
      &.one {
        background: #9C855B;
      }
      &.two {
        background: #1D2F45;
      }
      &.three {
        background: #712B5D;
      }
      &.four {
        background: #BC0600;
      }
      &.five {
        background: #E2A912;
      }
    }
    .section-inner {
      padding: 5rem 0;
      width: 1440px;
      box-shadow: 0 0 0 1px black;
      display: flex;
      justify-content: flex-start;
      // flex-wrap: wrap;
      .index-wrapper {
        margin: 0 5rem 0 0;
        h1 {
          margin: 0;
          font-size: 72px;
        }
      }
      .image-wrapper {
        margin: 0 5rem 0 0;
        img {
          box-shadow: 5px 5px 40px rgba(0,0,0,0.4);
          border: 1px solid rgba(0,0,0,0.3)
        }
      }
      .meta-wrapper {
        .sub-meta-wrapper {
          display: flex;
          justify-content: flex-start;
          width: 100%;
          div {
            margin: 0 2rem 0 0;
          }
        }
      }
    }
  }
</style>