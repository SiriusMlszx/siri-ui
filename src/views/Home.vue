<template>
  <div>
    <div class="topNavAndBanner">
      <TopNav/>
      <div class="banner">
        <h1>Peach UI</h1>
        <p class="actions">
          <a href="https://github.com/SiriusMlszx/peachui-siri">GitHub</a>
          <router-link to="/doc">探索</router-link>
        </p>
      </div>
    </div>
    <div class="features">
      <ul>
        <li>
          <svg>
            <use xlink:href="#icon-vue"></use>
          </svg>
          <h3>Vue3</h3>
          <p>使用了Composition API</p>
        </li>
        <li>
          <svg>
            <use xlink:href="#icon-ts"></use>
          </svg>
          <h3>TypeScript</h3>
          <p>源代码采用TypeScript书写</p>
        </li>
        <li>
          <svg>
            <use xlink:href="#icon-light"></use>
          </svg>
          <h3>代码易读</h3>
          <p>每个组件的源代码都极其简洁</p>
        </li>
      </ul>
    </div>
  </div>
</template>

<script lang="ts">
import TopNav from "../components/TopNav.vue";

export default {
  components: {TopNav}
};
</script>

<style lang="scss" scoped>
$pink: #fa7b83;
$border-radius: 4px;
$color: #f17070;
.features{
    margin: 64px auto;
  padding: 0 16px;

  @media (max-width: 500px){
    >ul{
      >li{
        padding-left: 30px;
        width: 100%;
      }
    }
  }
    @media (min-width: 800px){
      width: 800px;
      >ul{
        >li{
          width: 50%;
        }
      }
    }
    @media (min-width: 1200px){
      width: 1200px;
      >ul{
        >li{
          width: 33.3333%;
        }
      }
    }
    >ul{
      display: flex;
      flex-wrap: wrap;
      >li{
        margin: 16px 0;
        display: grid;
        justify-content: start;
        align-content: space-between;
        grid-template-areas:
            "icon title"
            "icon text";
        grid-template-columns: 80px auto;
        grid-template-rows: 1fr auto;

        >svg{
          grid-area: icon;
          width: 64px;
          height: 64px;
        }
        >h3{
          grid-area: title;
          font-size: 28px;
        }
        >p{
          grid-area: text;
        }
      }
    }
  }
.topNavAndBanner{
  background:  linear-gradient(45deg, rgba(255,248,205,1) 0%, rgba(251,195,168,1) 46%, rgba(248,152,148,1) 90%, rgba(248,144,144,1) 100%);
  clip-path: ellipse(80% 60% at 50% 40%);
}
.banner{
  color: $color;
  padding: 100px 0;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  > .actions{
    padding: 8px 0;
    a{
      margin: 20px 8px;
      background: $pink;
      color: white;
      display: inline-block;
      padding: 8px 24px;
      border-radius: $border-radius;
      &:hover{
        text-decoration: none;
      }
    }
  }
}
</style>