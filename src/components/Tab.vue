<script setup>
import { ref, onMounted } from 'vue';

const users = ref([]);
const activeTab = ref(0);

const fetchUserData = async () => {
  try {
    const response = await fetch('https://microsoftedge.github.io/Demos/json-dummy-data/64KB.json');
    const data = await response.json();
    users.value = data.slice(0, 5);
  } catch (error) {
    console.error('Error fetching data:', error);
  }
};

onMounted(fetchUserData);
</script>

<template>
  <div class="tab_wrap">
    <div class="button_wrap">
      <button v-for="(user, index) in users" :key="index" @click="activeTab = index" :class="{ 'active-tab': activeTab === index }">{{ user.name }}</button>
    </div>
    
    <div v-for="(user, index) in users" :key="index" v-show="activeTab === index" class="tab-content">
      <ul>
        <div class="li_item_wrap">
          <li><strong class="ret">Name:</strong></li><span>{{ user.name }}</span>
        </div>
        <div class="li_item_wrap">
          <li><strong class="ret">Language:</strong></li><span>{{ user.language }}</span>
        </div>
        <div class="li_item_wrap">
          <li><strong class="ret">Id:</strong></li><span>{{ user.id }}</span>
        </div>
        <div class="li_item_wrap">
          <li><strong class="ret">Bio:</strong></li><span>{{ user.bio }}</span>
        </div>
        <div class="li_item_wrap">
          <li><strong class="ret">Version:</strong></li><span>{{ user.version }}</span>
        </div>
      </ul>
      <div>
      </div>
    </div>
  </div>
</template>
<style lang="scss" scoped>
.tab_wrap{
  font-family: "Roboto", sans-serif;
}
.button_wrap{
  background-color: #e6e6e6;
  border-radius: 10px;
  margin-top: 15px;
  width: fit-content;
  button{
    color: #333;
    cursor: pointer;
    font-weight: 400;
    background-color: #e6e6e6;
    border-radius: 10px;
    font-size: 14px;
    line-height: 21.52px;
    border-style: none;
    outline-style: none;
    padding: 10px;
    margin: 0 7px;
  }
  button:first-child, button:last-child{
    margin: 0;
   }
  
}
.tab-content {
  padding: 0 5px;
  border: 1px solid #ccc;
  border-radius: 10px;
  margin-top: 15px;
  &.show {
    display: block;
  }
  ul{
    margin: 0;
  }
  li{
    width: 300px!important;
  }
  .li_item_wrap{
    display: flex;
    line-height: 21.52px;
    color: #333;
    font-weight: 400;
    padding: 10px 0;
    border-bottom: 1px solid #ccc;
      span{
      width: 1129px;
    }
  }
}
.active-tab {
  background-color: #1D1347!important;
  color: white!important;
}
@media (max-width: 540px){
  .button_wrap{
    flex-wrap: wrap;
    display: flex;
    align-items: center;
    justify-content: center;
  }
  span{
    width: auto;
    margin-left: 20px;
  }
  ul{
    padding-left: 20px;
  }
}
</style>
