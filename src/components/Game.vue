<template>

  <div id="top">
    {{top}}
  </div>
  <div id="middle">
    {{middle}}
  </div>
  <div id="bottom">
    <button @click="mountWord(q)" class="letter">{{q}}</button>
    <button @click="mountWord(w)" class="letter">{{w}}</button>
    <button @click="mountWord(e)" class="letter">{{e}}</button>
    <button @click="mountWord(r)" class="letter">{{r}}</button>
    <button @click="mountWord(t)" class="letter">{{t}}</button>
    <button @click="mountWord(y)" class="letter">{{y}}</button>
    <button @click="mountWord(u)" class="letter">{{u}}</button>
    <button @click="mountWord(i)" class="letter">{{i}}</button>
    <button @click="mountWord(o)" class="letter">{{o}}</button>
    <button @click="mountWord(p)" class="letter">{{p}}</button>
    <button @click="mountWord(a)" class="letter">{{a}}</button>
    <button @click="mountWord(s)" class="letter">{{s}}</button>
    <button @click="mountWord(d)" class="letter">{{d}}</button>
    <button @click="mountWord(f)" class="letter">{{f}}</button>
    <button @click="mountWord(g)" class="letter">{{g}}</button>
    <button @click="mountWord(h)" class="letter">{{h}}</button>
    <button @click="mountWord(j)" class="letter">{{j}}</button>
    <button @click="mountWord(k)" class="letter">{{k}}</button>
    <button @click="mountWord(l)" class="letter">{{l}}</button>
    <button @click="erraseWord()" class="letter">{{backspace}}</button>
    <button @click="mountWord(z)" class="letter">{{z}}</button>
    <button @click="mountWord(x)" class="letter">{{x}}</button>
    <button @click="mountWord(c)" class="letter">{{c}}</button>
    <button @click="mountWord(v)" class="letter">{{v}}</button>
    <button @click="mountWord(b)" class="letter">{{b}}</button>
    <button @click="mountWord(n)" class="letter">{{n}}</button>
    <button @click="mountWord(m)" class="letter">{{m}}</button>
    <button @click="submitAttemp()" class="letter">{{enter}}</button>

  </div>

</template>

<script>
export default {
  name: "Game",
  data: function () {
    return {
      top: 'Topo',
      middle: 'Meio',
      bottom: 'Bottom',
      q: 'Q',
      w: 'W',
      e: 'E',
      r: 'R',
      t: 'T',
      y: 'Y',
      u: 'U',
      i: 'I',
      o: 'O',
      p: 'P',
      a: 'A',
      s: 'S',
      d: 'D',
      f: 'F',
      g: 'G',
      h: 'H',
      j: 'J',
      k: 'K',
      l: 'L',
      backspace: 'APAGAR',
      z: 'Z',
      x: 'X',
      c: 'C',
      v: 'V',
      b: 'B',
      n: 'N',
      m: 'M',
      enter: 'ENTER',
      arrWords: Array
    };
  },
  mounted() {},
  methods: {
    //função para montar a palavra na linha
    mountWord: function(letter){
      this.arrWords += letter;
      console.log(this.arrWords);

    },
    //função para excluir a última letra adicionada na linha corrente
    erraseWord: function(){
    },
    //função para submeter uma tentativa
    submitAttemp: function(){},
  },
};
</script>

<style scoped>
#top{
  height: 10vh;
  width: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
}
#middle{
  height: 60vh;
  width: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
}
#bottom{
  height: 30vh;
  width: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>
