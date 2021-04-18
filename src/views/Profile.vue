<template>
  <div class="wrapper">
    <parallax class="section page-header header-filter" :style="headerStyle">
      <div class="container">
        <div class="md-layout">
          <div
            class="md-layout-item md-size-50 md-small-size-70 md-xsmall-size-100"
          >
            <br />
          </div>
        </div>
      </div>
    </parallax>
    <div class="main main-raised">
      <div class="section profile-content">
        <div class="container">
          <div class="md-layout">
            <div class="md-layout-item md-size-50 mx-auto">
              <div class="profile">
                <div class="avatar">
                  <img
                    :src="img"
                    alt="Circle Image"
                    class="img-raised rounded-circle img-fluid"
                  />
                </div>
                <div class="name">
                  <h3 class="title">Nosso Cardapio</h3>
                </div>
              </div>
            </div>
          </div>
        </div>

        <div class="container-flex">
            <Cardapio/>
        </div>
        
        <div class="container-flex">
          <template>
          <div class="md-layout md-alignment-center">
            <div class="md-layout-item md-size-50 mx-auto md-small-size-100">
              <div class="section">
                <div class="container text-center">
                  <md-card>
                    <carousel
                      :per-page="1"
                      loop
                      :speed="700"
                      autoplay
                      :autoplay-timeout="5000"
                      :mouse-drag="false"
                      navigationEnabled
                      navigationNextLabel="<i class='material-icons'>keyboard_arrow_right</i>"
                      navigationPrevLabel="<i class='material-icons'>keyboard_arrow_left</i>"
                    >
                      <slide>
                        <div class="carousel-caption">
                        </div>
                        <img :src="carousel1" alt="carousel1" />
                      </slide>
                      <slide>
                        <div class="carousel-caption">
                        </div>
                        <img :src="carousel2" alt="carousel2" />
                      </slide>
                    </carousel>
                  </md-card>
                </div>
              </div>
            </div>
            <div class="md-layout-item md-size-50 mx-auto md-small-size-100">
              <div class="section">
                <div class="container text-center">
                  <div class="md-layout">
                    <div class="md-layout-item md-size-66 md-xsmall-size-100 ml-auto mr-auto text-center">
                      <h2>Espaço Kids</h2>
                      <h4>
                        Temos um excelente espaço Kids para seus Baixinhos, Muito e seguro cheio de diversão para que seus filhos 
                        possam disfrutar do nosso restaurante.
                      </h4>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
          </template>
        </div>
        <div class="container-flex">
          <template>
          <div class="md-layout md-alignment-center">
            <div class="md-layout-item md-size-50 mx-auto md-small-size-100" v-if="$isMobile()">
              <div class="section">
                <div class="container text-center">
                  <md-card>
                    <carousel
                      :per-page="1"
                      loop
                      :speed="700"
                      autoplay
                      :autoplay-timeout="5000"
                      :mouse-drag="false"
                      navigationEnabled
                      navigationNextLabel="<i class='material-icons'>keyboard_arrow_right</i>"
                      navigationPrevLabel="<i class='material-icons'>keyboard_arrow_left</i>"
                    >
                      <slide>
                        <div class="carousel-caption">
                        </div>
                        <img :src="carousel3" alt="carousel1" />
                      </slide>
                      <slide>
                        <div class="carousel-caption">
                        </div>
                        <img :src="carousel4" alt="carousel2" />
                      </slide>
                    </carousel>
                  </md-card>
                </div>
              </div>
            </div>
            <div class="md-layout-item md-size-50 mx-auto md-small-size-100">
              <div class="section">
                <div class="container text-center">
                  <div class="md-layout">
                    <div
                      class="md-layout-item md-size-66 md-xsmall-size-100 ml-auto mr-auto text-center"
                    >
                      <h2>Nossos Drinks</h2>
                      <h4>
                        Aqui no restaurante coliseu contamos com uma variedade de drinks para que nossos clientes desfrutem,
                        nossos drinks vão de Caipirinhas até batidas de diversos sabores, além das diversas cachaças e outras bebidas.
                      </h4>
                    </div>
                  </div>
                </div>
              </div>
            </div>
            <div class="md-layout-item md-size-50 mx-auto md-small-size-100" v-if="!$isMobile()">
              <div class="section">
                <div class="container text-center">
                  <md-card>
                    <carousel
                      :per-page="1"
                      loop
                      :speed="700"
                      autoplay
                      :autoplay-timeout="5000"
                      :mouse-drag="false"
                      navigationEnabled
                      navigationNextLabel="<i class='material-icons'>keyboard_arrow_right</i>"
                      navigationPrevLabel="<i class='material-icons'>keyboard_arrow_left</i>"
                    >
                      <slide>
                        <div class="carousel-caption">
                        </div>
                        <img :src="carousel3" alt="carousel1" />
                      </slide>
                      <slide>
                        <div class="carousel-caption">
                        </div>
                        <img :src="carousel4" alt="carousel2" />
                      </slide>
                    </carousel>
                  </md-card>
                </div>
              </div>
            </div>
          </div>
          </template>
        </div>
        <div class="container-flex">
          <template>
            <div class="header-maps">
              <div class="md-layout md-gutter md-alignment-center">
                <h3>Endereço</h3>
              </div>
              <div class="md-layout md-small-size-100 md-xsmall-size-100 md-gutter md-alignment-center">
                <h4>R. José Bonifácio, 215 - Órfãs, Ponta Grossa - PR</h4>
              </div>
              <div class="ImgF">
                <iframe class="maps" src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3613.5252964312476!2d-50.169661784378704!3d-25.084073725463007!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x94e81bccf84fe875%3A0x282e02d089716507!2sRestaurante%20Coliseu!5e0!3m2!1spt-BR!2sbr!4v1616989221231!5m2!1spt-BR!2sbr" width="1920" height="700" style="border:0;" allowfullscreen="" loading="lazy"></iframe>            
              </div>

              <div class="md-layout  md-alignment-center">
                <div class="md-layout-item md-size-20 md-small-size-100 md-xsmall-size-100 md-gutter md-alignment-left footer-contacts img-footer" v-if="!$isMobile()">
                  <img
                    :src="img"
                    alt="Circle Image"
                    class="rounded-circle"
                    
                  />
                </div>
                <div class="md-layout-item md-size-10 md-small-size-100 md-xsmall-size-100 md-gutter md-alignment-left footer-contacts img-footer">
                  
                </div>
                <div class="md-layout-item md-size-25 md-small-size-100 md-xsmall-size-100 md-gutter md-alignment-center footer-contacts">                
                  <div>                   
                    <md-list class="md-triple-line">
                      <md-list-item>
                        <div class="title ">
                          <h1>Horário</h1>
                        </div>

                      </md-list-item>
                      <md-list-item>
                        <md-avatar>
                          <i class="far fa-clock icon-footer"></i>
                        </md-avatar>

                        <div class="md-list-item-text">
                          <h4>Terça a Sexta</h4>
                          <h4>18:00 as 23:00</h4>
                        </div>

                      </md-list-item>

                      <md-divider class="md-inset"></md-divider>

                        <md-list-item>
                        <md-avatar>
                          <i class="far fa-clock icon-footer"></i>
                        </md-avatar>

                        <div class="md-list-item-text">
                          <h4>Sabados</h4>
                          <h4>11:00 as 14:30<br>
                          18:00 as 23:00</h4>
                        </div>

                      </md-list-item>

                      <md-divider class="md-inset"></md-divider>

                      <md-list-item>
                        <md-avatar>
                          <i class="far fa-clock icon-footer"></i>
                        </md-avatar>

                        <div class="md-list-item-text">
                          <h4>Domingos</h4>
                          <h4>11:00 as 15:00</h4>
                        </div>

                      </md-list-item>
                    </md-list>
                  </div>
                </div>
                <div class="md-layout-item md-size-25 md-small-size-100 md-xsmall-size-100 md-gutter md-alignment-center footer-contacts">
                  <div>                   
                    <md-list class="md-triple-line">
                      <md-list-item>
                        <div class="title ">
                        <h1>Contato</h1>
                      </div>

                      </md-list-item>
                      <md-list-item>
                        <md-avatar>
                          <i class="fas fa-phone icon-footer"></i>
                        </md-avatar>

                        <div class="md-list-item-text">
                          <h4>Telefone</h4>
                          <h4>(42) 3623-4567</h4>
                        </div>

                      </md-list-item>

                      <md-divider class="md-inset"></md-divider>

                        <md-list-item>
                        <md-avatar>
                           <i class="fas fa-phone icon-footer"></i>
                        </md-avatar>

                        <div class="md-list-item-text">
                          <h4>Celular</h4>
                          <h4>(42) 99932-4589</h4>
                        </div>

                      </md-list-item>

                      <md-divider class="md-inset line-footer"></md-divider>

                       <md-list-item>
                        <md-avatar>
                          <i class="fas fa-envelope icon-footer"></i>
                        </md-avatar>

                        <div class="md-list-item-text">
                          <h4>E-mail</h4>
                          <h4>Restaurante.Coliseu@gmail.com</h4>
                        </div>

                      </md-list-item>

                    </md-list>
                  </div>
                </div>
              </div>
            </div>
          </template>
        </div>
        <a href="https://api.whatsapp.com/send?phone=5542999496389&text=Hola%21%20Quisiera%20m%C3%A1s%20informaci%C3%B3n%20sobre%20Varela%202." class="float" target="_blank">
          <i class="fab fa-whatsapp my-float"></i>
        </a>
      </div>
    </div>
  </div>
</template>

<script>
import Cardapio from "./components/Cardapio";

export default {
  components: {
    Cardapio
  },
  bodyClass: "profile-page",
  data() {
    return {

      // Fim das Variaveis do Pedido
      disabled:'',
      carousel1: require("@/assets/img/corousel/space_kids.jpg"),
      carousel2: require("@/assets/img/corousel/space_kids2.jpg"),
      carousel3: require("@/assets/img/corousel/Drink_full.png"),
      carousel4: require("@/assets/img/corousel/Drink_full2.png"),
      imageF: require("@/assets/img/bg.jpg"),
    };
  },
  props: {
    header: {
      type: String,
      default: require("@/assets/img/prato2.jpg"),
    },
    img: {
      type: String,
      default: require("@/assets/img/faces/logo.jpg"),
    },
  },
  methods: {
    getEnderecoByCep(){

      let api = new XMLHttpRequest();
       if (api.readyState == 4 && api.status == 200) {
        var myArr = JSON.parse(this.responseText);
        myFunction(myArr);
      }
      api.open("GET",'https://viacep.com.br/ws/' + this.form.PedidoCep +'/json',true);
      api.send();

          console.log(api.XMLHttpRequest.response)
      function myFunction(arr) {
      }
    },
    validatePedido() {
      this.$v.$touch()

      if (!this.$v.$invalid) {
        this.TelegramSendMessage()
      }
    },
    submitItem(evt){
        evt.preventDefault();
        document.getElementById("FormPedido").submit();
    },
    getValidationClass (fieldName) {
      const field = this.$v.form[fieldName]

      if (field) {
        return {
          'md-invalid': field.$invalid && field.$dirty
        }
      }
    }
  },
  computed: {
    headerStyle() {
      return {
        backgroundImage: `radial-gradient(circle, rgba(122,121,121,0) 11%, rgba(5,5,5,0.8323704481792717) 67%), url(${this.header})`,
      };
    },
    bgImage() {
      return {
        backgroundImage: `url(${this.header})`
      };
    }
  }
};
</script>

<style lang="scss" scoped>
.mt{
  margin-top:5px;
}
.mt2{
  margin-top:15px;
}
.maps{
  height: 400px;
}
.header-maps{
  background-color: #6a0201;
  text-decoration-color: white;
}
.header-maps h1{
  color: white;
}
.header-maps h3{
  color: white;
}
.header-maps h4{
  color: white;
}
.header-maps ul{
  background-color: #6a0201 !important;
}
.footer-contacts{
  height: 100% !important;
  padding-left: 15px;
}
.icon-footer{
  color: white;
}
.md-divider.md-theme-default {
   background-color: white !important;
}
.float{
	position:fixed;
	width:60px;
	height:60px;
	bottom:40px;
	right:40px;
	background-color:#25d366;
	color:#FFF;
	border-radius:50px;
	text-align:center;
  font-size:30px;
	box-shadow: 2px 2px 3px #999;
  z-index:100;
}

.my-float{
	margin-top:16px;
  color: white;
}

  .md-layout-item{
    padding-right: 15px;
    padding-left: 15px;
  }



@media screen and (max-width: 600px) and (min-width: 400px)  {
    .img-footer{
  display: none;
}



}

</style>
