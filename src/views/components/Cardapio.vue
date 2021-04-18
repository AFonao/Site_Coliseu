<template>
    <div class="container">
        <div class="profile-tabs">
            <tabs
                :tab-name="[
                'Bovino',
                'Aves',
                'Peixes',
                'Macarrão',
                'Lasanhas',
                'Porções',
                ]"
                :tab-icon="[icon1, icon2, icon3, icon4, icon5, icon6]"
                plain
                nav-pills-icons
                color-button="my-class"
            >
                <template slot="tab-pane-1">
                    <div class="md-layout">
                        <div class="md-layout-item md-size-30 md-small-size-100 md-xsmall-size-100" v-for="item of tabPane1" :key="item.id">
                            <Card 
                                :titulo="item.nome" 
                                :imagem="item.image"
                                :descricao="item.descricao"
                                :tempo_preparo="item.tempo_preparo"
                            >
                                <md-button class="md-success" @click="ADD_Item(item.id)" slot="btn">Adicionar ao Carrinho</md-button>
                            </Card>
                        </div>
                    </div>
                </template>
                <template slot="tab-pane-2">
                     <div class="md-layout">
                        <div class="md-layout-item md-size-30 md-small-size-100 md-xsmall-size-100" v-for="item of tabPane2" :key="item.id">
                            <Card 
                                :titulo="item.nome" 
                                :imagem="item.image"
                                :descricao="item.descricao"
                                :tempo_preparo="item.tempo_preparo"
                            >
                                <md-button class="md-success" @click="ADD_Item(item.id)" slot="btn">Adicionar ao Carrinho</md-button>
                            </Card>
                        </div>
                    </div>
                </template>
                <template slot="tab-pane-3">
                     <div class="md-layout">
                        <div class="md-layout-item md-size-30 md-small-size-100 md-xsmall-size-100" v-for="item of tabPane3" :key="item.id">
                            <Card 
                                :titulo="item.nome" 
                                :imagem="item.image"
                                :descricao="item.descricao"
                                :tempo_preparo="item.tempo_preparo"
                            >
                                <md-button class="md-success" @click="ADD_Item(item.id)" slot="btn">Adicionar ao Carrinho</md-button>
                            </Card>
                        </div>
                    </div>
                </template>
                <template slot="tab-pane-4">
                     <div class="md-layout">
                        <div class="md-layout-item md-size-30 md-small-size-100 md-xsmall-size-100" v-for="item of tabPane4" :key="item.id">
                            <Card 
                                :titulo="item.nome" 
                                :imagem="item.image"
                                :descricao="item.descricao"
                                :tempo_preparo="item.tempo_preparo"
                            >
                                <md-button class="md-success" @click="ADD_Item(item.id)" slot="btn">Adicionar ao Carrinho</md-button>
                            </Card>
                        </div>
                    </div>
                </template>
                <template slot="tab-pane-5">
                     <div class="md-layout">
                        <div class="md-layout-item md-size-30 md-small-size-100 md-xsmall-size-100" v-for="item of tabPane5" :key="item.id">
                            <Card 
                                :titulo="item.nome" 
                                :imagem="item.image"
                                :descricao="item.descricao"
                                :tempo_preparo="item.tempo_preparo"
                            >
                                <md-button class="md-success" @click="ADD_Item(item.id)" slot="btn">Adicionar ao Carrinho</md-button>
                            </Card>
                        </div>
                    </div>
                </template>
                 <template slot="tab-pane-6">
                     <div class="md-layout">
                        <div class="md-layout-item md-size-30 md-small-size-100 md-xsmall-size-100" v-for="item of tabPane6" :key="item.id">
                            <Card 
                                :titulo="item.nome" 
                                :imagem="item.image"
                                :descricao="item.descricao"
                                :tempo_preparo="item.tempo_preparo"
                            >
                                <md-button class="md-success" @click="ADD_Item(item.id)" slot="btn">Adicionar ao Carrinho</md-button>
                            </Card>
                        </div>
                    </div>
                </template>
            </tabs>
        </div>
        <div v-if="StoreCart.length > 0">
            <a href="#/carrinho" class="float-shopping">
                <md-badge :md-content="StoreCart.length"/>
                <i class="fas fa-shopping-cart my-float-shopping"></i>
            </a>
        </div>
    </div>
</template>

<script>
    import { Tabs } from "@/components";
    import { Card } from "@/components";
    export default {
        components: {
            Tabs,
            Card
        },
        bodyClass: "Cardapio",
        data(){
            return{

                valor:2,

                //Produtos
                StoreCart: JSON.parse( localStorage.getItem("storeCart") ) ? JSON.parse( localStorage.getItem("storeCart") ) : [] ,
                icon1: require("@/assets/img/icons/BV.png"),
                icon2: require("@/assets/img/icons/AV.png"),
                icon3: require("@/assets/img/icons/PX.png"),
                icon4: require("@/assets/img/icons/MS.png"),
                icon5: require("@/assets/img/icons/LS.png"),
                icon6: require("@/assets/img/icons/PR.png"),
                tabPane1: [
                    {
                    id: "1",
                    image: require("@/assets/img/pratos/bovinas/parmegiana_alcatra.jpg"),
                    nome: "Parmegiana de Alcatra",
                    valor: '110',
                    descricao: 'Prato Feito do Miolo de Alcatra Com queijo e molho vermelho',
                    tempo_preparo: '40 - 50 minutos'
                    },
                    {
                    id: "2",
                    image: require("@/assets/img/pratos/bovinas/alcatra_grelhado.jpg"),
                    nome: "Alcatra Grelhado",
                    valor: '100',
                    descricao: 'Prato Feito do Miolo de Alcatra Com quijo e molho vermelho',
                    tempo_preparo: '40 - 50 minutos'
                    },
                    {
                    id: "3",
                    image: require("@/assets/img/pratos/bovinas/picanha_grelhada.jpg"),
                    nome: "Picanha Grelhada",
                    valor: '130',
                    descricao: 'Prato Feito do Miolo de Alcatra Com quijo e molho vermelho',
                    tempo_preparo: '40 - 50 minutos'
                    },
                    {
                    id: "4",
                    image: require("@/assets/img/pratos/bovinas/parmegiana_alcatra.jpg"),
                    nome: "Filé Grelhado",
                    valor: '110',
                    descricao: 'Prato Feito do Miolo de Alcatra Com quijo e molho vermelho',
                    tempo_preparo: '40 - 50 minutos'
                    },
                ],
                tabPane2: [
                    {
                    id: "1",
                    image: require("@/assets/img/pratos/aves/frango_parmegiana.jpg"),
                    nome: "Parmegiana de Frango",
                    valor: '110',
                    descricao: 'Prato Feito do Miolo de Alcatra Com queijo e molho vermelho',
                    tempo_preparo: '40 - 50 minutos'
                    },
                    {
                    id: "2",
                    image: require("@/assets/img/pratos/aves/frango_grelhado.jpg"),
                    nome: "Frango Grelhado",
                    valor: '100',
                    descricao: 'Prato Feito do Miolo de Alcatra Com quijo e molho vermelho',
                    tempo_preparo: '40 - 50 minutos'
                    },
                    {
                    id: "3",
                    image: require("@/assets/img/pratos/aves/frango_4_queijos.jpg"),
                    nome: "Frango quatro queijos",
                    valor: '130',
                    descricao: 'Prato Feito do Miolo de Alcatra Com quijo e molho vermelho',
                    tempo_preparo: '40 - 50 minutos'
                    }
                ],
                tabPane3: [
                    {
                    id: "1",
                    image: require("@/assets/img/pratos/peixes/tilapia_parmegiana.jpg"),
                    nome: "Parmegiana de Tilapia",
                    valor: '110',
                    descricao: 'Prato Feito do Miolo de Alcatra Com queijo e molho vermelho',
                    tempo_preparo: '40 - 50 minutos'
                    },
                    {
                    id: "2",
                    image: require("@/assets/img/pratos/peixes/tilapia_grelhada.jpg"),
                    nome: "Tilapia Grelhada",
                    valor: '100',
                    descricao: 'Prato Feito do Miolo de Alcatra Com quijo e molho vermelho',
                    tempo_preparo: '40 - 50 minutos'
                    },
                    {
                    id: "3",
                    image: require("@/assets/img/pratos/peixes/tilapia_camarao.jpg"),
                    nome: "Tilapia ao molho de camarão",
                    valor: '130',
                    descricao: 'Prato Feito do Miolo de Alcatra Com quijo e molho vermelho',
                    tempo_preparo: '40 - 50 minutos'
                    }
                ],
                tabPane4: [
                    {
                    id: "1",
                    image: require("@/assets/img/pratos/macarrao/sugo.jpg"),
                    nome: "Ao Sugo",
                    valor: '110',
                    descricao: 'Prato Feito do Miolo de Alcatra Com queijo e molho vermelho',
                    tempo_preparo: '40 - 50 minutos'
                    },
                    {
                    id: "2",
                    image: require("@/assets/img/pratos/macarrao/bolonhesa.jpg"),
                    nome: "Bolonhesa",
                    valor: '100',
                    descricao: 'Prato Feito do Miolo de Alcatra Com quijo e molho vermelho',
                    tempo_preparo: '40 - 50 minutos'
                    },
                    {
                    id: "3",
                    image: require("@/assets/img/pratos/macarrao/carbonara.jpg"),
                    nome: "Carbonara",
                    valor: '130',
                    descricao: 'Prato Feito do Miolo de Alcatra Com quijo e molho vermelho',
                    tempo_preparo: '40 - 50 minutos'
                    },
                    {
                    id: "4",
                    image: require("@/assets/img/pratos/macarrao/4_queijos.jpg"),
                    nome: "Quatro queijos",
                    valor: '130',
                    descricao: 'Prato Feito do Miolo de Alcatra Com quijo e molho vermelho',
                    tempo_preparo: '40 - 50 minutos'
                    }
                ],
                tabPane5: [
                    {
                    id: "1",
                    image: require("@/assets/img/pratos/lasanhas/bolonhesa.jpg"),
                    nome: "Bolonhesa",
                    valor: '110',
                    descricao: 'Prato Feito do Miolo de Alcatra Com queijo e molho vermelho',
                    tempo_preparo: '40 - 50 minutos'
                    }
                ],
                tabPane6: [
                    {
                    id: "1",
                    image: require("@/assets/img/pratos/porcoes/tilapia.jpg"),
                    nome: "Tilapia",
                    valor: '110',
                    descricao: 'Prato Feito do Miolo de Alcatra Com queijo e molho vermelho',
                    tempo_preparo: '40 - 50 minutos'
                    },
                    {
                    id: "2",
                    image: require("@/assets/img/pratos/porcoes/provolone.jpg"),
                    nome: "Provolone",
                    valor: '100',
                    descricao: 'Prato Feito do Miolo de Alcatra Com quijo e molho vermelho',
                    tempo_preparo: '40 - 50 minutos'
                    },
                    {
                    id: "3",
                    image: require("@/assets/img/pratos/porcoes/frango_passarinho.jpg"),
                    nome: "Frango a Passarinho",
                    valor: '130',
                    descricao: 'Prato Feito do Miolo de Alcatra Com quijo e molho vermelho',
                    tempo_preparo: '40 - 50 minutos'
                    },
                    {
                    id: "4",
                    image: require("@/assets/img/pratos/porcoes/alcatra.jpg"),
                    nome: "Alcatra",
                    valor: '130',
                    descricao: 'Prato Feito do Miolo de Alcatra Com quijo e molho vermelho',
                    tempo_preparo: '40 - 50 minutos'
                    }
                ],
            }
        },
        methods:{
            ADD_Item(id) {
                let context = this;
                if(this.StoreCart.find(item => item === id)){
                    this.$alert(
                    "Prato já adicionado no Carrinho.",
                    "Atenção",
                    "warning",
                    { 
                        confirmButtonColor: "#6a0201"
                    }
                    )
                }else{
                    
                    this.$prompt(
                    "Informe a quantidade",
                    "1",
                    "Pedido",
                    "question",
                    { 
                        input: "number",
                        confirmButtonText: "Adicionar",
                        cancelButtonText: "Cancelar",
                        confirmButtonColor: "#6a0201"
                    }
                    )
                    .then((r) => {
                        context.StoreCart.push(id);
                        localStorage.setItem("storeCart",JSON.stringify(this.StoreCart));
                    })
                    .catch(() => console.log("canceled"));
                    
                }
            },
        }
    }
</script>

<style scoped>
 .md-card{
     margin-left: 8px !important;
 }
 .float-shopping{
	position:fixed;
	width:60px;
	height:60px;
	bottom:110px;
	right:40px;
	background-color:#6a0201;
	color:#FFF;
	border-radius:50px;
	text-align:center;
    font-size:30px;
	box-shadow: 2px 2px 3px #999;
    z-index:100;
}


.my-float-shopping{
	margin-top:16px;
    color: white;
}



    .mobile-bottom-nav{
        position:fixed;
        bottom:0;
        left:0;
        right:0;
        z-index:1000;
        
        will-change:transform;
        transform: translateZ(0);
        
        display:flex;	
        
        height:50px;
        
        box-shadow: 0 -2px 5px -2px #333;
        background-color:#fff;
    }
</style>
