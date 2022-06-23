<template>

  <div id="top">
    <div class="conteudo">
    <i class="fa-solid fa-circle-chevron-up"></i>
  </div>
  <div class="conteudo">
    {{topo}}
  </div>
  <div class="conteudo">
    <div>
      <i class="fa-solid fa-chart-simple"></i>
      <i class="fa-solid fa-gear"></i>
    </div>
  </div>
  </div>
  <div id="middle">
    <div id="words-table">
      <div class="words-row" v-for="(line, index) in arrWords">
        <div class="letter-table" v-for="(item, index) in line">{{item}}</div>
      </div>
    </div>
  </div>
  <div id="bottom">
    <div id="keyboard">
      <div class="keyboard-line">
        <button @click="mountWord(q)" class="letter btn btn-outline-primary">{{q}}</button>
        <button @click="mountWord(w)" class="letter btn btn-outline-primary">{{w}}</button>
        <button @click="mountWord(e)" class="letter btn btn-outline-primary">{{e}}</button>
        <button @click="mountWord(r)" class="letter btn btn-outline-primary">{{r}}</button>
        <button @click="mountWord(t)" class="letter btn btn-outline-primary">{{t}}</button>
        <button @click="mountWord(y)" class="letter btn btn-outline-primary">{{y}}</button>
        <button @click="mountWord(u)" class="letter btn btn-outline-primary">{{u}}</button>
        <button @click="mountWord(i)" class="letter btn btn-outline-primary">{{i}}</button>
        <button @click="mountWord(o)" class="letter btn btn-outline-primary">{{o}}</button>
        <button @click="mountWord(p)" class="letter btn btn-outline-primary">{{p}}</button>
      </div>
      <div class="keyboard-line">
        <button @click="mountWord(a)" class="letter btn btn-outline-primary">{{a}}</button>
        <button @click="mountWord(s)" class="letter btn btn-outline-primary">{{s}}</button>
        <button @click="mountWord(d)" class="letter btn btn-outline-primary">{{d}}</button>
        <button @click="mountWord(f)" class="letter btn btn-outline-primary">{{f}}</button>
        <button @click="mountWord(g)" class="letter btn btn-outline-primary">{{g}}</button>
        <button @click="mountWord(h)" class="letter btn btn-outline-primary">{{h}}</button>
        <button @click="mountWord(j)" class="letter btn btn-outline-primary">{{j}}</button>
        <button @click="mountWord(k)" class="letter btn btn-outline-primary">{{k}}</button>
        <button @click="mountWord(l)" class="letter btn btn-outline-primary">{{l}}</button>
        <button @click="erraseWord()" id="backspace" class="btn btn-outline-primary"><i class="fa-solid fa-delete-left"></i></button>
      </div>
      <div class="keyboard-line">
        <button @click="mountWord(z)" class="letter btn btn-outline-primary">{{z}}</button>
        <button @click="mountWord(x)" class="letter btn btn-outline-primary">{{x}}</button>
        <button @click="mountWord(c)" class="letter btn btn-outline-primary">{{c}}</button>
        <button @click="mountWord(v)" class="letter btn btn-outline-primary">{{v}}</button>
        <button @click="mountWord(b)" class="letter btn btn-outline-primary">{{b}}</button>
        <button @click="mountWord(n)" class="letter btn btn-outline-primary">{{n}}</button>
        <button @click="mountWord(m)" class="letter btn btn-outline-primary">{{m}}</button>
        <button @click="submitAttemp()" id="enter" class="btn btn-outline-primary">{{enter}}</button>
      </div>
    </div>

  </div>

</template>

<script>
export default {
  name: "Game",
  data: function () {
    return {
      topo: 'DESCUBRA',
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
      backspace: '',
      z: 'Z',
      x: 'X',
      c: 'C',
      v: 'V',
      b: 'B',
      n: 'N',
      m: 'M',
      enter: 'ENTER',
      arrWords: [
        ['', '', '', '', ''],
        ['', '', '', '', ''],
        ['', '', '', '', ''],
        ['', '', '', '', ''],
        ['', '', '', '', ''],
        ['', '', '', '', '']
      ]
    };
  },
  mounted() {},
  methods: {
    //função para montar a palavra na linha
    mountWord: function(letter){
      this.arrWords.unshift(letter);
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

*{
  /* font-family: 'Font Awesome 5'; */
}
#top{
  height: 10vh;
  width: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  font-family: "Impact", Times, serif;
  font-size: 40px;
  color: #337ab7;
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

.letter{
  width: 3em;
  height: 3.5em;
  font-weight: bolder;
  font-family: 'Font Awesome 5';
}

#enter, #backspace{
  height: 3.5em;
  font-weight: bolder;
}

#backspace{
  width: 3em;
}

#keyboard{
  width: 100%;
  justify-content: center;
  display: flex;
  flex-direction: column;
  align-items: center;
}

.keyboard-line{
  padding: 0.5em;
}

.letter, #backspace, #enter{
  margin-inline: 0.25em;
}

#words-table{
  height: 80%;
  width: 30%;
  display: grid;
  grid-gap: 0.5em;
  margin: 0;
  padding: 0;
}

.words-row{
  display: grid;
  grid-template-columns: repeat(5, 20fr);
  grid-gap: 0.5em;
  font-size: 1em;
  margin: 0;
  line-height: 0;
}

.letter-table{
    font-weight: bolder;
    color: #FAFAFF;
    background-color: #337ab7;
    border-radius: 10%;
    display: flex;
    box-sizing: border-box;
    justify-content: center;
    align-items: center;
    font-size: 2em;
    line-height: 1em;
    text-transform: uppercase;
    --happy-jump: 55%;
    cursor: pointer;
}

button{
  color: #337ab7;
  border-color: #337ab7;
}

button:hover{
  background-color: #337ab7;
}
.conteudo {
  margin: 80px;
}

</style>
