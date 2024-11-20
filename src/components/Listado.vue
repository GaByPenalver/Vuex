<template>
    <h1>Tienda 32 Bits</h1>
    <h2>Lista de juegos</h2>
    <table>
    <thead>
        <tr>
          <th>CÓDIGO</th>
          <th>NOMBRE</th>
          <th>STOCK</th>
          <th>PRECIO</th>
          <th>ACCIONES</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="game in games" :key="game.codigo">
          <td>{{ game.codigo }}</td>
          <td>{{ game.nombre }}</td>
          <td>{{ game.stock }}</td>
          <td>{{ game.precio }}</td>
          <td>
            <button @click="updateStock(game.codigo, '+')">+</button>
            <button @click="updateStock(game.codigo, '-')">-</button>
          </td>
        </tr>
      </tbody>
    </table>
  </template>
  
  <script>
  import { mapGetters, mapActions } from "vuex";
  
  export default {
    name: "Listado",
    computed: {
      ...mapGetters(["games"]),
    },
    methods: {
      ...mapActions(["modifyStock"]),
      updateStock(codigo, quantity) {
        this.modifyStock({ codigo, quantity });
      },
    },
  };
  </script>
  
  <style>
  h1 {
    text-align: center;
    font-size: 50px;
  } 
  h2 {
    text-align: center;
    font-size: 30px;
  } 

  table {
    border-collapse: collapse;
    padding: 15px;
    margin-top: 150px;
    margin-left: 70px;
  }
  th, td {
    border: 1px solid #000;
    padding: 0 50px;
    height: 30px;
  }
  th {
    background-color: #6A1E55;
    color: aqua;
  }
  button {
  margin-left: 20px;
  text-align: center;
  font-size: 20px;
  height: 20px;
  border-radius: 4px; 
  }
  </style>