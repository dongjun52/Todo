<template>
<div class="wrap">
  <div class="header">
    <p>Todo shopping mall</p>
  </div>
  <div class="container">
    <div class="product_list">
      <ul>
        <li v-for="todo in todos" v-bind:key="todo.id">
          <div class="img_section">
            <img src="@/assets/images/imac.jpg" alt="">
          </div>
          <div class="info_section">
            <p>상품명: {{todo.title}}</p>
            <p>가격: {{todo.body}}</p>
          </div>
          <div class="btn_list">
            <button class="buy">구매하기</button>
            <button class="modi">수정하기</button>
          </div>
        </li>
      </ul>
    </div>
  </div>
  <div class="footer">
    <p>Create by Andy</p>
  </div>
</div>
</template>

<script>
import axios from 'axios';
import {ref} from 'vue';


export default {
    name:'Todo',
    setup() {
      const todos = ref([]);

      const getTodos = async () => {
        const data = await axios.get('https://jsonplaceholder.typicode.com/posts')
        todos.value = data.data;
      }

      getTodos();

      return {
        todos,
      }
    },
}
</script>

<style>
  * {margin: 0; padding: 0;}
  ul,li {list-style: none;}
  img {max-width: 100%; vertical-align: top;}

  .wrap {
    width: 480px;
    margin: 0 auto;
  }

  .header {
    background: navy;
    color: whitesmoke;
    padding: 10px 0;
  }

  .product_list ul li .info_section {
    background: darkgrey;
    padding: 20px 15px;
    font-weight: bold;
    line-height: 1.5;
  }

  .product_list ul li .btn_list {
    display: flex;
    justify-content: space-between;
  }

  .product_list ul li .btn_list > button {
    width: 50%;
    height: 40px;
    border: none;
    cursor: pointer;
  }
  
  .product_list ul li .btn_list .buy {
    background: olive;
  }

  .product_list ul li .btn_list .modi {
    background: tomato;
  }

  .footer {
    background: indigo;
    color: #fff;
    padding: 5px 0;
  }
</style>