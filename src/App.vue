<script setup>
        import { ref } from 'vue'
        
       
        const produtos = ref([
          {
            id: 1,
            nome: 'Chevrolet Spin',
            preco: 106560.00,
            quant: 1,
            lugares: '7',
            ano: '2012',
            img: "Spin.jpg"
          },
          {
            id: 2,
            nome: ' Jeep Commander',
            preco: 245490.00,
            quant: 1,
            lugares: '7',
            ano: '2021',
            img: "Jeep_Commander.jpeg"
           
           
          },
          {
            id: 3,
            nome: 'Caoa Chery Tiggo 8',
            preco: 18240.00,
            quant: 1,
            lugares: '7',
            ano: '2023', 
            img: "Tiggo.jpeg"
           
           
          },
          {
            id: 4,
            nome: 'Toyota SW4',
            preco: 385451.00,
            quant: 1,
            lugares: '7',
            ano: '2022',
            img: "Toyota.jpeg"
           
           
          },
          {
            id: 5,
            nome: 'Audi Q7',
            preco: 520169.00,
            quant: 1,
            lugares: "7",
            ano: '2022',
            img: "Q7.jpg",
            
            
           
          },
          {
            id: 6,
            nome: 'Volvo XC90 Plus T8',
            preco: 519950.00  ,
            quant: 1,
            lugares: '7',
            ano: '2023',
            img: "Volvo_XC90.jpg"
           
          },
          {
            id: 7,
            nome: 'Mitsubishi Pajero Sport',
            preco: 331536.00,
            quant: 1,
            lugares: '7',
            ano: '2022',
            img: "Mitsubishi.jpg"
           
          },
          {
            id: 8,
            nome: 'Land Rover Discovery Sport',
            preco: 344490.00,
            quant: 1,
            lugares: '7',
            ano: '2022',
            img: "Land_Rover.jpg"
           
          },
          {
            id: 9,
            nome: 'Chevrolet Trailblazer Premier',
            preco: 343056.00,
            quant: 1,
            lugares: '7',
            ano: '2023',
            img: "Traiblazer.jpg"
           
          },
          {
            id: 10,
            nome: ' Mercedes-Benz GLB 200',
            preco: 327368.00,
            quant: 1,
            lugares: '7',
            ano: '2022',
            img: "mercedes-benz.jpg"
          },
          {
            id: 11,
            nome: 'Kia Sorento 3.5 V6   ',
            preco: 211502.00,
            quant: 1,
            lugares: '7',
            ano: '2020',
            img: "Kia_Sorento .jpg"

           
          },
          {
            id: 12,
            nome: 'Kia Carnival 3.5 V6',
            preco: 544000.00,
            quant: 1,
            lugares: '8',
            ano: '2022',
            img: "Carnival_2023.jpg"

           
          }
        ])
       
        const carrinho = ref({
          items: [],
          valorTotal: 0,
        })
       
        function carrinho_Compras() {
         
        }
       
        function adicionarPeca(pos) {
            produtos.value[pos].quant++
        }
       
        function removerPeca(pos) {
          if (produtos.value[pos].quant > 1) {
            produtos.value[pos].quant--
          }
       
        }
       
        function adicionar_Carrinho(i) {
          const produto = produtos.value[i]
          carrinho.value.items.push({...produto, total: produto.preco * produto.quant})
          carrinho.value.valorTotal += produto.preco * produto.quant
        }
       
       
        </script>
        
       
        <template>
          <nav>
            <div class="Menu">
              <ul>
            <li><a href="">Family Cars</a></li>
 
            </ul>        </div>
          </nav>
            <button @click="carrinho_Compras" class="carrinho">
              Carrinho
             
            </button>
          <div class="produtos">
            <div v-for="(produto, i) in produtos" :key="i" class="card-produto">
              <img :src="produto.img">
              <h2>{{ produto.nome }}</h2>
              <p> R$ {{ produto.preco.toFixed(2).replace('.',',') }}</p>
              <p> Quantidade: {{ produto.quant }}</p>
              <div class="botes">
                <button @click="adicionarPeca(i)">+</button>
                <button @click="removerPeca(i)">-</button>
                <button @click="adicionar_Carrinho(i)">Adicionar ao carrinho</button>
              </div>
            </div>
          </div>
          <div>
            {{ carrinho }}
          </div>
        </template>
       
        <style scoped>
        ul {
        list-style-type: none;
      margin: 0;
      padding: 0;
      overflow: hidden;
      background-color:#232A33;
}

li {
  float:inline-end;
}

li a {
  display:block;
  color: white;
  text-align: center;
  padding: 19px 19px;
  text-decoration:overline underline;
  background-color:#232A33;
  font-family: 'Times New Roman', Times, serif;
   border: 8px #232A33 solid;
  border-radius: 8px;
  font-size: 20px;
  
}

li a:hover {
  background-color:#2F4159;
}
        
        .card-produto {
          width: 300px;
          height: 450px;
          border-radius: 10px;
          box-shadow: #939599 0px 5px 15px;
          display: flex;
          font-family: 'Times New Roman', Times, serif;
          color:#B3D5F2;
          text-decoration-line:underline;
          text-decoration-color:#D9D9D9;  
          flex-direction: column;
          align-items: center;
          background-color: #232A33;
        }
       
        .card-produto img {
          margin-top: 40%;
          width: 80%;
        }
        .produtos {
          margin: 200px;
          margin-top: 30px;
          margin-left: 10%;
          display: grid;
          grid-template-columns: repeat(4, 27%);
          grid-auto-rows: 40%;
        }
        .carrinho {
          width: 8%;
          margin-left: 10%;
          padding: 10px;
          background-color:#232A33;
          border-radius: 5px;
          border: 1px solid gray;
          font-family: 'Times New Roman', Times, serif;
          font-size: 20px;
          transition: all 0.2s;

        }
        .carrinho:hover{
          transition: 0.2s;
          transform: scale(1.1);
          background-color:#2F4159 ;
        }
       
       
        .img-carrinho {
          width: 20px;
          height: 20px;
        }
       
        p {
          color:azure;
        }
       
        h2, p {
          margin: 4px;
        }
       
        button {
          background-color:#595959 ;
          border-radius: 4px;
          border: 1px solid gray;
          font-family: 'Times New Roman', Times, serif;
          margin: 2px;
          color: #D9D9D9;
        }
       
        button:hover {
          background-color: #2F4159;
        }
       
        </style>
   

