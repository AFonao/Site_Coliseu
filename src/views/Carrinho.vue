<template>
  <div class="wrapper">
    <parallax class="section page-header header-filter" :style="headerStyle">
      <div class="container">
        <div class="md-layout">
          <div
            class="md-layout-item md-size-50 md-small-size-70 md-xsmall-size-100"
          >
            <h1 class="title">Restaurante Coliseu</h1>
            <h4>Um novo sabor a cada prato!</h4>
            <br />
          </div>
        </div>
      </div>
    </parallax>
    <div class="main main-raised">
      <div class="section section-basic">
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
                  <h3 class="title">Carrinho</h3>
                </div>
              </div>
            </div>
          </div>
        </div>
        <div class="section section-basic">
          <div class="container-fluid">
            <template>
                <div  class="md-layout">
                    <div class="md-layout-item md-size-50 md-small-size-100 md-xsmall-size-100">
                        <md-card>
                            <md-card-header>
                                <div class="md-title">Pedido</div>
                            </md-card-header>
                            <md-card-content>
                                <template>
                                    <div  v-for="item of itens" :key="item.id">

                                      <md-list class="md-triple-line">
                                          <md-list-item>
                                          <md-avatar>
                                              <img :src="item.image" alt="People">
                                          </md-avatar>

                                          <div class="md-list-item-text">
                                              <span>{{item.nome}}</span>
                                              <span>quantidade:1</span>
                                          </div>

                                          <md-button @click="REMOVE_Item(item.id)">
                                              <md-icon class="md-danger">delete</md-icon>
                                          </md-button>
                                          </md-list-item>
                                      </md-list>
                                      <md-divider class="md-inset"></md-divider>
          
                                    </div>
                                    <div class="md-alignment-right .mt">
                                      <h4 class="mt md-alignment-right" v-if="taxaEntrega">Taxa de entrega R${{taxaEntrega}},00</h4>
                                      <h3 class="mt md-alignment-right">Total R${{Total}},00</h3>
                                    </div>
                                    <div v-if="itens == ''">
                                      <h3>Sem Itens!</h3>
                                    </div>
                                </template>
                            </md-card-content>
                        </md-card>
                    </div>

                    <div class="md-layout-item md-size-50 md-small-size-100 md-xsmall-size-100">
                        <md-card>
                            <md-card-header>
                                <div class="md-title">Entrega</div>
                            </md-card-header>
                            <md-card-content>
                                <template>
                                    <form novalidate class="md-layout" id="FormPedido" @submit.prevent="validatePedido">
                                        <div class="md-layout-item">
                                                
                                            <div class="md-layout-item md-layout md-gutter mt">

                                                <div class="md-layout-item md-small-size-100 md-xsmall-size-100 mt">
                                                    <md-field :class="getValidationClass('PedidoNome')">
                                                        <md-input placeholder="Nome" name="PedidoNome" id="PedidoNome" v-model="form.PedidoNome"></md-input>
                                                        <span class="md-error" v-if="!$v.form.PedidoNome.required">Nome é um campo Obrigatório</span>
                                                        <span class="md-error" v-else-if="!$v.form.PedidoNome.minLength">Tamanho do Campo é invalido!</span>
                                                    </md-field>
                                                </div>

                                                <div class="md-layout-item md-small-size-100 md-xsmall-size-100 mt">
                                                    <md-field :class="getValidationClass('PedidoTelefone')">
                                                        <md-input placeholder="Telefone" name="PedidoTelefone" id="PedidoTelefone" v-model="form.PedidoTelefone"></md-input>
                                                        <span class="md-error" v-if="!$v.form.PedidoTelefone.required">Telefone é um campo Obrigatório</span>
                                                        <span class="md-error" v-else-if="!$v.form.PedidoTelefone.minLength">Tamanho do Campo é invalido!</span>
                                                    </md-field>
                                                </div>

                                                <div class="md-layout-item md-size-100 md-small-size-100 md-xsmall-size-100 mt">
                                                    <div class="flex-column">
                                                        <md-radio v-model="entrega" :value="false">Entregar</md-radio>
                                                        <md-radio v-model="entrega" :value="true">Retirar no Balcão</md-radio>
                                                    </div>
                                                </div>
                                            </div>

                                            <div class="md-layout-item md-layout md-gutter">
                                                <div class="md-layout-item md-size-30 md-small-size-100 md-xsmall-size-100 mt">
                                                    <md-field>
                                                        <md-input placeholder="CEP" v-bind:disabled ="entrega == true" @change="getEnderecoByCep()" v-model="form.PedidoCep"></md-input>
                                                    </md-field>
                                                </div>
                                                <div class="md-layout-item md-size-70 md-small-size-100 md-xsmall-size-100 mt">
                                                    <md-field :class="getValidationClass('PedidoRua')">
                                                        <md-input placeholder="Rua" v-bind:disabled ="entrega == true"  v-model="form.PedidoRua" id="rua"></md-input>
                                                        <span class="md-error" v-if="!$v.form.PedidoRua.required">Rua é um campo Obrigatório</span>
                                                    </md-field>
                                                </div>
                                                <div class="md-layout-item md-size-50 md-small-size-100 md-xsmall-size-100 mt">
                                                    <md-field :class="getValidationClass('PedidoNumero')">
                                                        <md-input placeholder="Número" v-bind:disabled ="entrega == true" v-model="form.PedidoNumero" id="numero"></md-input>
                                                        <span class="md-error" v-if="!$v.form.PedidoNumero.required">Número é um campo Obrigatório</span>
                                                    </md-field>
                                                </div>
                                                <div class="md-layout-item md-size-50 md-small-size-100 md-xsmall-size-100 mt">
                                                    <md-field :class="getValidationClass('PedidoBairro')">
                                                        <md-select placeholder="Bairro" v-bind:disabled ="entrega == true" v-model="form.PedidoBairro" id="bairro" v-on:blur="ItensCariinho()">
                                                            <md-option v-for="option of BairrosEntrega" v-bind:value="option.nome" :key="option.id">{{ option.nome }}</md-option>
                                                        </md-select>
                                                        <span class="md-error" v-if="!$v.form.PedidoBairro.required">Bairro é um campo Obrigatório</span>
                                                    </md-field>
                                                </div>
                                                <div class="md-layout-item md-size-100 md-small-size-100 md-xsmall-size-100 mt">
                                                    <md-field>
                                                        <md-input placeholder="Complemento" v-bind:disabled ="entrega == true" v-model="form.PedidoComplemento"></md-input>
                                                    </md-field>
                                                </div>
                                                <div class="md-layout-item md-size-100 md-small-size-100 md-xsmall-size-100 mt2" v-if="entrega == false && taxaEntrega">
                                                    <h4>Taxa de Entrega R$: {{taxaEntrega}}</h4>
                                                </div>
                                                <div class="md-layout-item md-size-100 md-small-size-100 md-xsmall-size-100 mt2">
                                                    <label>!Pagamento é feito para o motoboy no ato da entrega</label>
                                                    <div class="flex-column">
                                                        <md-radio v-model="dinheiro" :value="true">Dinheiro</md-radio>
                                                        <md-radio v-model="dinheiro" :value="false">Cartão</md-radio>
                                                    </div>
                                                </div>
                                                <div class="md-layout-item md-size-100 md-small-size-100 md-xsmall-size-100 mt" v-show=dinheiro>
                                                  <md-field>
                                                      <md-input placeholder="Troco Para" v-model="form.PedidoTroco"></md-input>
                                                  </md-field>
                                              </div>
                                            </div>



                                            <div class="md-layout-item md-layout md-gutter md-alignment-left mt">
                                                <div class="md-layout-item  md-small-size-100 md-xsmall-size-100">
                                                <md-button type="submit" class="md-success" >Comprar</md-button>
                                                </div>
                                            </div>

                                        </div>
                                    </form>
                                </template>
                            </md-card-content>
                        </md-card>
                    </div>
                </div>
            </template>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { validationMixin } from 'vuelidate'
  import {
    required,
    email,
    minLength,
    maxLength,
    requiredIf 
  } from 'vuelidate/lib/validators';
  import axios from 'axios';

export default {
    mixins: [validationMixin],
    bodyClass: "profile-page",
    async created() {
        const res = await axios.get('http://localhost:8081/#/Entrega.json');
        this.ValorEntrega = res.data;
    },
    data() {
        return {

        // Telgram
        ApiTelegramToken : '1785514959:AAFrYiKI9zzc2xoUdOfprLqA5RYq39IIdQc',
        ApiTelegramChatId : '-551967027',
        ApiTelegramUrl: 'https://api.telegram.org/bot',
        // Fim Telgram

        form: {
            PedidoQuantidade: null,
            PedidoNome: null,
            PedidoTelefone: null,
            PedidoItem: null,
            PedidoTamanho:'Inteira',
            PedidoRua:null,
            PedidoNumero:null,
            PedidoBairro:null,
            PedidoComplemento:null,
            PedidoCep:null,
            PedidoTroco:null
        },
        img: require("@/assets/img/faces/logo.jpg"),
        header: require("@/assets/img/prato2.jpg"),
        entrega: true,
        dinheiro: false,
        StoreCart: JSON.parse( localStorage.getItem("storeCart") ) ? JSON.parse( localStorage.getItem("storeCart") ) : [] ,
        itens:[],
        Total:0,
        ValorEntrega: [],
        tabPane1: [
          {
            id: "1",
            image: require("@/assets/img/pratos/bovinas/parmegiana_alcatra.jpg"),
            nome: "Parmegiana de Alcatra",
            valor: 110,
            descricao: 'Prato Feito do Miolo de Alcatra Com quijo e molho vermelho',
            tempo_preparo: '40 - 50 minutos'
          },
          {
            id: "2",
            image: require("@/assets/img/pratos/bovinas/alcatra_grelhado.jpg"),
            nome: "Alcatra Grelhado",
            valor: 100,
            descricao: 'Prato Feito do Miolo de Alcatra Com quijo e molho vermelho',
            tempo_preparo: '40 - 50 minutos'
          },
          {
            id: "3",
            image: require("@/assets/img/pratos/bovinas/picanha_grelhada.jpg"),
            nome: "Picanha Grelhada",
            valor: 130,
            descricao: 'Prato Feito do Miolo de Alcatra Com quijo e molho vermelho',
            tempo_preparo: '40 - 50 minutos'
          },
          {
            id: "4",
            image: require("@/assets/img/pratos/bovinas/parmegiana_alcatra.jpg"),
            nome: "Filé Grelhado",
            valor: 110,
            descricao: 'Prato Feito do Miolo de Alcatra Com quijo e molho vermelho',
            tempo_preparo: '40 - 50 minutos'
          },
        ],
        taxaEntrega : 0,
        BairrosEntrega: [ 
          {
            id:1,
            nome:'Oficinas',
            valor:12
          },
          {
            id:2,
            nome:'Santa Paula',
            valor:13
          },
          {
            id:3,
            nome:'Uvaranas',
            valor:15
          },
        ]
    }
  },
  computed: {
    headerStyle() {
      return {
        backgroundImage: `radial-gradient(circle, rgba(122,121,121,0) 11%, rgba(5,5,5,0.8323704481792717) 67%), url(${this.header})`,
      };
    },
  },
  validations: {
      form: {
        // PedidoQuantidade: {
        //   required,
        //   minLength: minLength(1)
        // },
        PedidoNome: {
          required,
          minLength: minLength(3)
        },
        PedidoTelefone: {
          required,
          minLength: minLength(3)
        },
        PedidoRua:{
          required: requiredIf(function() {
            return this.entrega == false
          }),
        },
        PedidoNumero:{
          required: requiredIf(function() {
            return this.entrega == false
          }),
        },
        PedidoBairro:{
          required: requiredIf(function() {
            return this.entrega == false
          }),
        }
      }
  },
   methods: {
        getEnderecoByCep(){
            let api = new XMLHttpRequest();
            let retorno = '';
            let Contexto = this;
            api.onreadystatechange = function() {
                if (api.readyState == XMLHttpRequest.DONE) {
                    retorno = JSON.parse(api.response);
                    Contexto.form.PedidoRua = retorno.logradouro;
                    Contexto.form.PedidoBairro =  retorno.bairro;
                    Contexto.ItensCariinho();
                }
            }
            api.open("GET",'https://viacep.com.br/ws/' + this.form.PedidoCep +'/json',true);
            api.send();
        },
        validatePedido() {
            this.$v.$touch()
            console.log(this.$v.$invalid)
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
        },
        ItensCariinho(){
          let result = [];
          let total = 0;
          let array = this.tabPane1;
          if(this.StoreCart){
              this.StoreCart.forEach(function(el, i){
                result.push(array.find( item => item.id === el ));
              });
              result.forEach(function(el, i){
                total += el.valor
              });
              if(this.form.PedidoBairro){
                let valorEntrega = this.BairrosEntrega.find( bairro => bairro.nome == this.form.PedidoBairro);
                total += valorEntrega.valor;
                this.taxaEntrega = valorEntrega.valor;
              }
              this.Total = total;
              this.itens = result;
          }
        },
        REMOVE_Item(index) {
          this.$confirm(
            "Desejá Realmente Remover este item do Carrinho?.",
            "",
            "question",
            {
              confirmButtonText: "Sim",
              cancelButtonText: "Não",
              confirmButtonColor: "#6a0201"
            }
          )
          .then((r) => {
            document.getElementById("pre-loader").className += "pre-loader";
            this.StoreCart.splice(this.StoreCart.indexOf(index),1);
            localStorage.setItem("storeCart",JSON.stringify(this.StoreCart));
            setTimeout(function(){
                document.getElementById("pre-loader").classList.remove("pre-loader");
            }, 1000);
            this.ItensCariinho();
          })
          .catch(() => {
              console.log("OK not selected.");
          });
        },
        
    // Telegram Methods
    TelegramSendMessage(){
      document.getElementById("pre-loader").className += "pre-loader";
      let message = '';
      let produtos = '';
      let pagamento = '';
      let retorno = '';
      let contexto = this;
      let alert = this.$alert(
                        "Pedido Efetuado com Sucesso!",
                        "Agora é só aguardar",
                        "success",
                        {
                          confirmButtonColor: "#6a0201"
                        }
                      );

      this.itens.forEach(function (item,index) {
          produtos += `------------------------ %0A` 
          produtos += `Pedido Item: ${item.nome}%0A`
          produtos += `Item Tamanho : Inteira %0A`
          produtos += `Pedido Quantidade:1 %0A`  
      })

      if(!this.entrega){
        pagamento += this.dinheiro ? 'Forma de Pagamento:Dinheiro%0A' + 'Troco Para:' + this.form.PedidoTroco : 'Forma de Pagamento:Cartão' +'%0A' 
      }

      if(this.entrega){
        //Balcão
        message = `NOVO PEDIDO%0ANome: ${this.form.PedidoNome}%0ATelefone:${this.form.PedidoTelefone}%0ATipo de Retirada: Balcao%0A${produtos}`;
      }else{
        //Entrega
        message = `NOVO PEDIDO%0ANome: ${this.form.PedidoNome}%0ATelefone:${this.form.PedidoTelefone}%0ATipo de Retirada: Entrega%0ARua:  ${this.form.PedidoRua}%0ANúmero:  ${this.form.PedidoNumero}%0ABairro:  ${this.form.PedidoBairro}%0AComplemento: ${this.form.PedidoComplemento}%0A${pagamento}%0A${produtos}`;
      }

      let api = new XMLHttpRequest();
      api.onreadystatechange = function() {
          if (api.readyState == XMLHttpRequest.DONE) {
              document.getElementById("pre-loader").classList.remove("pre-loader");
              retorno = JSON.parse(api.response);
              localStorage.removeItem("storeCart");
              contexto.itens = [];
              alert;
          }
      }
      api.open("GET",this.ApiTelegramUrl + this.ApiTelegramToken + '/sendMessage?chat_id=' + this.ApiTelegramChatId + '&text=' + message + '&parse_mode=html',true);
      api.send();         
    },
   },
   beforeMount(){
        this.ItensCariinho()
    },
};
</script>

<style lang="scss" scoped>

  .mt{
    margin-top:10px;
  }

  .md-layout-item{
    padding-right: 15px;
    padding-left: 15px;
  }

</style>
