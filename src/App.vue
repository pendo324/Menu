<template>
  <div id="app">
    <div class="showcase">
      <Showcase v-for="item in menuItems" :key="item.id" :selected-item="item.selected">
        <img :src="item.showcaseImage">
      </Showcase>
    </div>
    <div id="menu">
      <MenuItem v-for="item in menuItems" :key="item.id" :selected-item="item.selected">
        {{item.content}}
      </MenuItem>
    </div>
  </div>
</template>

<script>
import Showcase from './components/MenuShowcase';
import MenuItem from './components/MenuItem';

export default {
  name: 'app',
  components: {
    Showcase,
    MenuItem
  },
  data: () => ({
    currentItem: 0,
    menuItems: [
      { content: 'Test 1', id: 1, showcaseImage: 'https://dummyimage.com/512&text=1', selected: true },
      { content: 'Test 2', id: 2, showcaseImage: 'https://dummyimage.com/512&text=2', selected: false },
      { content: 'Test 3', id: 3, showcaseImage: 'https://dummyimage.com/512&text=3', selected: false },
      { content: 'Test 4', id: 4, showcaseImage: 'https://dummyimage.com/512&text=4', selected: false }
    ]
  }),
  mounted: function () {
    setInterval(() => {
      console.log(this.currentItem);
      this.menuItems[this.currentItem].selected = false;
      this.currentItem = (this.currentItem + 1) % this.menuItems.length;
      this.menuItems[this.currentItem].selected = true;
      console.log(this.currentItem);
    }, 5000);
  }
};
</script>

<style>
#app {
  display: flex;
  flex-direction: row;
  margin-top: 60px;
}

#showcase {
  flex-basis: 40%;
}

#menu {
  flex-basis: 60%;
}

.active {
    position: absolute;
    opacity: 0;
    transition: opacity 1s;
}
</style>
