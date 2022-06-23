<template>

  <div id="top">

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
const attemps = {
  'line1':[
    {'attempSubmited' : '', 'attempSuccess' : ''}
  ],
  'line2':[
    {'attempSubmited' : '', 'attempSuccess' : ''}
  ],
  'line3':[
    {'attempSubmited' : '', 'attempSuccess' : ''}
  ],
  'line4':[
    {'attempSubmited' : '', 'attempSuccess' : ''}
  ],
  'line5':[
    {'attempSubmited' : '', 'attempSuccess' : ''}
  ],
  'line6':[
    {'attempSubmited' : '', 'attempSuccess' : ''}
  ], 
};
export default {
  name: "Game",
  data: function () {
    return {
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
      blank: '',
      arrWords: [
        ['', '', '', '', ''],
        ['', '', '', '', ''],
        ['', '', '', '', ''],
        ['', '', '', '', ''],
        ['', '', '', '', ''],
        ['', '', '', '', '']
      ],
      attemps: {
        'line0':[
          {'attempSubmited' : false, 'attempSuccess' : false}
        ],
        'line1':[
          {'attempSubmited' : false, 'attempSuccess' : false}
        ],
        'line2':[
          {'attempSubmited' : false, 'attempSuccess' : false}
        ],
        'line3':[
          {'attempSubmited' : false, 'attempSuccess' : false}
        ],
        'line4':[
          {'attempSubmited' : false, 'attempSuccess' : false}
        ],
        'line5':[
          {'attempSubmited' : false, 'attempSuccess' : false}
        ],
      },
    };
  },
  mounted() {},
  methods: {
    //função para montar a palavra na linha
    mountWord: function(letter){
      for(let i =  0; i < this.arrWords.length; i++){
        for(let z = 0; z < this.arrWords[0].length; z++){
          if(this.arrWords[i][4] != '' && !this.verifyAttemp(i)){
            return;
          }
          else if(this.arrWords[i][z] == ''){
            this.arrWords[i][z] = letter;
            return;
          }
          
        }
      }

    },
    verifyAttemp: function(lineNumber){
      if(lineNumber == 0)return this.attemps.line0.attempSubmited;
      else if(lineNumber == 1) return this.attemps.line1.attempSubmited;
      else if(lineNumber == 2) return this.attemps.line2.attempSubmited;
      else if(lineNumber == 3) return this.attemps.line3.attempSubmited;
      else if(lineNumber == 4) return this.attemps.line4.attempSubmited;
      else return this.attemps.line5.attempSubmited;
    },
    //função para excluir a última letra adicionada na linha corrente
    erraseWord: function(){
      if(!this.verifyAttemp(0)) this.erraseLetter(0);
      else if(!this.verifyAttemp(1)) this.erraseLetter(1);
      else if(!this.verifyAttemp(2)) this.erraseLetter(2);
      else if(!this.verifyAttemp(3)) this.erraseLetter(3);
      else if(!this.verifyAttemp(4)) this.erraseLetter(4);
      else if(!this.verifyAttemp(5)) this.erraseLetter(5);

    },
    erraseLetter: function(lineNumber){
      for(let i =  this.arrWords[0].length; i >= 0; i--){
        if(this.arrWords[lineNumber][i] !== '' && !(this.arrWords[lineNumber][i] === undefined)){
          this.arrWords[lineNumber][i] = '';
          return;
        } 
      }
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
    font-size: 3em;
    text-transform: uppercase;
    --happy-jump: 55%;
    cursor: pointer;
}

button{
  color: #337ab7;
  border-color: #337ab7;
  outline:none!important; 
}

button:hover{
  background-color: #337ab7;
}
</style>
