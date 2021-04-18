<template>
    <div>
      <!-- <md-card v-if="$isMobile()">
        <md-card-media-cover md-solid>
          <md-card-media md-ratio="4:8">
            <img :src="imagem" alt="Coffee House">
          </md-card-media>

          <md-card-area>
            <md-card-header>
              <div class="md-title">{{titulo}}</div>
              <div class="md-subhead">R$110,00</div>
            </md-card-header>

            <md-card-actions>
              <slot name="btn"></slot>
            </md-card-actions>
            
          </md-card-area>
        </md-card-media-cover>
      </md-card> -->

      <md-card v-if="$isMobile()">
        <md-card-header>
          <md-card-header-text>
            <div class="md-title">{{titulo}}</div>
                <div class="md-subhead">R$110,00</div>
          </md-card-header-text>

          <md-card-media  md-medium>
            <img :src="imagem">
          </md-card-media>
        </md-card-header>
        <md-card-content>
            <h3 class="md-subheading">Tempo Médio de Preparo</h3>
            <div class="card-reservation">  
              <h4><md-icon>access_time</md-icon> : {{tempo_preparo}}</h4>
            </div>
        </md-card-content>

        <md-card-actions>
          <slot name="btn"></slot>
        </md-card-actions>
      </md-card>

      <md-card class="md-card-example" v-else>
        <md-card-area md-inset>
            <md-card-media md-ratio="16:9">
                <img :src="imagem" alt="Coffee House">
            </md-card-media>

            <md-card-header>
                <h2 class="md-title">{{titulo}}</h2>
                <div class="md-subhead">
                    <span>R$110,00</span>
                </div>
            </md-card-header>

            <md-card-content>
                {{descricao}}
            </md-card-content>
        </md-card-area>

        <md-card-content>
            <h3 class="md-subheading">Tempo Médio de Preparo</h3>
            <div class="card-reservation">
                <md-icon>access_time</md-icon>
                <h4>{{tempo_preparo}}</h4>
            </div>
        </md-card-content>

        <md-card-actions>
            <slot name="btn"></slot>
        </md-card-actions>
      </md-card>
    </div>
</template>

<script>
  export default {
    name: 'Card',
    props:['titulo','imagem','descricao','tempo_preparo']
  }
</script>

<style lang="scss" scoped>
  .md-card {
    width: 100%;
    margin: 10px;
    display: inline-block;
    vertical-align: top;
    margin-left: 10px;
  }

  .md-card-example {
    .md-subhead {
      .md-icon {
        $size: 16px;

        width: $size;
        min-width: $size;
        height: $size;
        font-size: $size !important;
      }

      span {
        vertical-align: middle;
      }
    }

    .card-reservation {
      margin-top: 8px;
      display: flex;
      align-items: center;
      justify-content: space-between;
      margin-left: 10px;

      .md-icon {
        margin: 8px;
      }
    }

    .md-button-group {
      display: flex;

      .md-button {
        min-width: 60px;
        border-radius: 2px;
      }
    }
  }
</style>
