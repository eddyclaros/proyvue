<template>
<div class="ejemplovue">
  <div class="container">
            <input type="text" v-model="nombre" @keydown.enter="add()" class="form-control">
            {{ nombre }}
            <hr>
            {{ nombres }}
            <hr>
            <select name="" id="" v-model="idnombre" class="form-control">
                <option value="0">Seleccionar</option>
                <option v-for="(nom,index) in nombres" :key="index" :value="index" v-text="nom"></option>
            </select>
            <p>{{ idnombre }}</p>
            <button class="btn btn-info" @click="contador()">contar</button>
            {{ sum }}
            <hr>
            <div>
                <input type="radio" id="uno" value="Uno" v-model="picked">
                <label for="uno">Uno</label>
                <br>
                <input type="radio" id="Dos" value="Dos" v-model="picked">
                <label for="Dos">Dos</label>
                <br>
                <span>Eligió: {{ picked }}</span>
              </div>

            <div v-if="picked=='Uno'" class="from-group">
                <h3>muestra este texto</h3>

            </div>
            <input type="checkbox" name="" id="" v-model="hasError">
            <div class="static form-control"
                v-bind:class="{ active: isActive, 'text-danger': hasError }"> cambio de class
            </div>
        </div>
</div>

</template>
<script>
export default {
  name: 'ejemplosVue',
  data () {
    return {
      nombre: '',
      sum: 0,
      resultado: 0,
      idnombre: 0,
      picked: '',
      isActive: true,
      hasError: false,
      nombres: []
    }
  },
  computed: {
  },
  methods: {
      add () {
          let me= this
          if( me.nombre!=''){
              me.nombres.push(me.nombre)
              me.nombre=''
          }
      },
      contador(){
          let me=this
          me.sum++
      },
      esActivo(index){
          let me=this
          //console.log('index',index,'actual',me.actual)
          //if()
          return index===me.actual;
      },
  },
  mounted(){
      console.log("montado")
  }
}
</script>

