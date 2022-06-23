<template>

  <div id="top">
    <div class="conteudo">
      <div>
        <i class="fa-solid fa-circle-question margin10"></i>
        <i class="fa-solid fa-circle-chevron-up"></i>
      </div>
    </div>
    <div class="conteudo">
      {{topo}}
    </div>
    <div class="conteudo">
      <div>
        <i class="fa-solid fa-chart-simple margin10"></i>
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
      dicioWords:
        [
          {
            "sagaz": "sagaz",
            "amago": "âmago",
            "negro": "negro",
            "exito": "êxito",
            "mexer": "mexer",
            "termo": "termo",
            "senso": "senso",
            "nobre": "nobre",
            "algoz": "algoz",
            "afeto": "afeto",
            "plena": "plena",
            "etica": "ética",
            "mutua": "mútua",
            "tenue": "tênue",
            "sutil": "sutil",
            "vigor": "vigor",
            "aquem": "aquém",
            "fazer": "fazer",
            "porem": "porém",
            "audaz": "audaz",
            "sanar": "sanar",
            "secao": "seção",
            "assim": "assim",
            "inato": "inato",
            "cerne": "cerne",
            "ideia": "ideia",
            "fosse": "fosse",
            "desde": "desde",
            "poder": "poder",
            "moral": "moral",
            "torpe": "torpe",
            "muito": "muito",
            "honra": "honra",
            "justo": "justo",
            "futil": "fútil",
            "gozar": "gozar",
            "anexo": "anexo",
            "razao": "razão",
            "etnia": "etnia",
            "quica": "quiçá",
            "sobre": "sobre",
            "icone": "ícone",
            "sonho": "sonho",
            "tange": "tange",
            "egide": "égide",
            "lapso": "lapso",
            "mutuo": "mútuo",
            "expor": "expor",
            "amigo": "amigo",
            "haver": "haver",
            "habil": "hábil",
            "casal": "casal",
            "porra": "porra",
            "tempo": "tempo",
            "seara": "seara",
            "pesar": "pesar",
            "avido": "ávido",
            "entao": "então",
            "dengo": "dengo",
            "posse": "posse",
            "bocal": "boçal",
            "genro": "genro",
            "coser": "coser",
            "ardil": "ardil",
            "causa": "causa",
            "corja": "corja",
            "dizer": "dizer",
            "prole": "prole",
            "paria": "pária",
            "detem": "detém",
            "tenaz": "tenaz",
            "dever": "dever",
            "saber": "saber",
            "obice": "óbice",
            "digno": "digno",
            "graca": "graça",
            "crivo": "crivo",
            "apice": "ápice",
            "ansia": "ânsia",
            "animo": "ânimo",
            "orgia": "orgia",
            "brado": "brado",
            "ceder": "ceder",
            "comum": "comum",
            "gleba": "gleba",
            "sendo": "sendo",
            "temor": "temor",
            "assaz": "assaz",
            "culto": "culto",
            "atroz": "atroz",
            "mundo": "mundo",
            "pauta": "pauta",
            "censo": "censo",
            "fugaz": "fugaz",
            "ainda": "ainda",
            "cozer": "cozer",
            "denso": "denso",
            "valha": "valha",
            "nenem": "neném",
            "vicio": "vício",
            "forte": "forte",
            "estar": "estar",
            "vulgo": "vulgo",
            "reves": "revés",
            "pudor": "pudor",
            "regra": "regra",
            "dogma": "dogma",
            "louco": "louco",
            "criar": "criar",
            "banal": "banal",
            "impor": "impor",
            "round": "round",
            "saude": "saúde",
            "jeito": "jeito",
            "tenro": "tenro",
            "pifio": "pífio",
            "atras": "atrás",
            "desse": "desse",
            "ordem": "ordem",
            "apraz": "apraz",
            "pedir": "pedir",
            "merce": "mercê",
            "clava": "clava",
            "reaca": "reaça",
            "usura": "usura",
            "prosa": "prosa",
            "viril": "viril",
            "juizo": "juízo",
            "feliz": "feliz",
            "servo": "servo",
            "sabio": "sábio",
            "homem": "homem",
            "coisa": "coisa",
            "ontem": "ontem",
            "manso": "manso",
            "presa": "presa",
            "xibiu": "xibiu",
            "falar": "falar",
            "forma": "forma",
            "cunho": "cunho",
            "devir": "devir",
            "fluir": "fluir",
            "afago": "afago",
            "meiga": "meiga",
            "ebrio": "ébrio",
            "mesmo": "mesmo",
            "plato": "platô",
            "vendo": "vendo",
            "serio": "sério",
            "limbo": "limbo",
            "guisa": "guisa",
            "magoa": "mágoa",
            "visar": "visar",
            "pleno": "pleno",
            "heroi": "herói",
            "temer": "temer",
            "acaso": "acaso",
            "puder": "puder",
            "cisma": "cisma",
            "valor": "valor",
            "bruma": "bruma",
            "lugar": "lugar",
            "posso": "posso",
            "exodo": "êxodo",
            "afins": "afins",
            "obvio": "óbvio",
            "gerar": "gerar",
            "impio": "ímpio",
            "obter": "obter",
            "certo": "certo",
            "crise": "crise",
            "matiz": "matiz",
            "praxe": "praxe",
            "senil": "senil",
            "havia": "havia",
            "venia": "vênia",
            "fluxo": "fluxo",
            "enfim": "enfim",
            "todos": "todos",
            "ritmo": "ritmo",
            "tedio": "tédio",
            "alibi": "álibi",
            "abrir": "abrir",
            "uniao": "união",
            "tomar": "tomar",
            "garbo": "garbo",
            "valia": "valia",
            "reter": "reter",
            "pulha": "pulha",
            "visao": "visão",
            "FALSO": "FALSO",
            "parvo": "parvo",
            "facil": "fácil",
            "vital": "vital",
            "grato": "grato",
            "bravo": "bravo",
            "favor": "favor",
            "vivaz": "vivaz",
            "prumo": "prumo",
            "laico": "laico",
            "parco": "parco",
            "genio": "gênio",
            "olhar": "olhar",
            "burro": "burro",
            "legal": "legal",
            "ameno": "ameno",
            "possa": "possa",
            "reles": "reles",
            "levar": "levar",
            "tecer": "tecer",
            "obito": "óbito",
            "casta": "casta",
            "tesao": "tesão",
            "prime": "prime",
            "selar": "selar",
            "anelo": "anelo",
            "fator": "fator",
            "ranco": "ranço",
            "morte": "morte",
            "nocao": "noção",
            "rogar": "rogar",
            "citar": "citar",
            "facam": "façam",
            "farsa": "farsa",
            "noite": "noite",
            "adiar": "adiar",
            "achar": "achar",
            "cabal": "cabal",
            "coeso": "coeso",
            "cisao": "cisão",
            "epico": "épico",
            "falta": "falta",
            "nicho": "nicho",
            "ouvir": "ouvir",
            "fardo": "fardo",
            "forca": "força",
            "ativo": "ativo",
            "viver": "viver",
            "sinto": "sinto",
            "brega": "brega",
            "gente": "gente",
            "imune": "imune",
            "exato": "exato",
            "haste": "haste",
            "amplo": "amplo",
            "passo": "passo",
            "sonso": "sonso",
            "lavra": "lavra",
            "sulco": "sulco",
            "dubio": "dúbio",
            "cesta": "cesta",
            "tendo": "tendo",
            "leigo": "leigo",
            "sesta": "sesta",
            "unico": "único",
            "revel": "revel",
            "labor": "labor",
            "deter": "deter",
            "gesto": "gesto",
            "vemos": "vemos",
            "calma": "calma",
            "vadia": "vadia",
            "arduo": "árduo",
            "humor": "humor",
            "linda": "linda",
            "atuar": "atuar",
            "feixe": "feixe",
            "rever": "rever",
            "ciume": "ciúme",
            "pobre": "pobre",
            "otica": "ótica",
            "tende": "tende",
            "carma": "carma",
            "outro": "outro",
            "igual": "igual",
            "ponto": "ponto",
            "hiato": "hiato",
            "toada": "toada",
            "velho": "velho",
            "ajuda": "ajuda",
            "ideal": "ideal",
            "claro": "claro",
            "sonsa": "sonsa",
            "debil": "débil",
            "vacuo": "vácuo",
            "ambos": "ambos",
            "terno": "terno",
            "remir": "remir",
            "varao": "varão",
            "cauda": "cauda",
            "fusao": "fusão",
            "probo": "probo",
            "senao": "senão",
            "leito": "leito",
            "fonte": "fonte",
            "marco": "marco",
            "jovem": "jovem",
            "advem": "advém",
            "inata": "inata",
            "capaz": "capaz",
            "horda": "horda",
            "xeque": "xeque",
            "terra": "terra",
            "tenra": "tenra",
            "relva": "relva",
            "ficar": "ficar",
            "algum": "algum",
            "velar": "velar",
            "cacar": "caçar",
            "serie": "série",
            "apoio": "apoio",
            "farao": "farão",
            "lider": "líder",
            "anuir": "anuir",
            "vazio": "vazio",
            "vimos": "vimos",
            "rigor": "rigor",
            "tanto": "tanto",
            "verso": "verso",
            "cocar": "coçar",
            "dorso": "dorso",
            "entre": "entre",
            "botar": "botar",
            "frase": "frase",
            "pouco": "pouco",
            "massa": "massa",
            "signo": "signo",
            "sente": "sente",
            "cruel": "cruel",
            "coesa": "coesa",
            "prece": "prece",
            "mocao": "moção",
            "virus": "vírus",
            "ambas": "ambas",
            "morar": "morar",
            "fauna": "fauna",
            "peste": "peste",
            "raiva": "raiva",
            "casto": "casto",
            "covil": "covil",
            "feito": "feito",
            "minha": "minha",
            "preso": "preso",
            "credo": "credo",
            "ciclo": "ciclo",
            "papel": "papel",
            "corno": "corno",
            "faina": "faina",
            "impar": "ímpar",
            "torco": "torço",
            "lazer": "lazer",
            "furor": "furor",
            "docil": "dócil",
            "flora": "flora",
            "brisa": "brisa",
            "vetor": "vetor",
            "chata": "chata",
            "maior": "maior",
            "arido": "árido",
            "trama": "trama",
            "aceso": "aceso",
            "beata": "beata",
            "houve": "houve",
            "pegar": "pegar",
            "blase": "blasé",
            "adeus": "adeus",
            "manha": "manha",
            "vulto": "vulto",
            "nossa": "nossa",
            "setor": "setor",
            "liame": "liame",
            "banzo": "banzo",
            "breve": "breve",
            "vasto": "vasto",
            "birra": "birra",
            "senda": "senda",
            "salvo": "salvo",
            "seita": "seita",
            "ardor": "ardor",
            "livro": "livro",
            "meses": "meses",
            "peixe": "peixe",
            "morro": "morro",
            "visse": "visse",
            "pecha": "pecha",
            "atomo": "átomo",
            "chuva": "chuva",
            "prado": "prado",
            "antro": "antro",
            "reger": "reger",
            "comer": "comer",
            "prono": "prono",
            "sorte": "sorte",
            "plano": "plano",
            "avaro": "avaro",
            "segue": "segue",
            "saiba": "saiba",
            "ocaso": "ocaso",
            "rezar": "rezar",
            "foder": "foder",
            "pajem": "pajem",
            "carro": "carro",
            "nunca": "nunca",
            "alias": "aliás",
            "saida": "saída",
            "otimo": "ótimo",
            "aureo": "áureo",
            "ancia": "anciã",
            "junto": "junto",
            "mudar": "mudar",
            "acima": "acima",
            "chulo": "chulo",
            "seria": "séria",
            "serao": "serão",
            "sinal": "sinal",
            "opcao": "opção",
            "fitar": "fitar",
            "jazia": "jazia",
            "fruir": "fruir",
            "parar": "parar",
            "treta": "treta",
            "fugir": "fugir",
            "nacao": "nação",
            "puxar": "puxar",
            "bando": "bando",
            "andar": "andar",
            "grupo": "grupo",
            "prazo": "prazo",
            "motim": "motim",
            "gerir": "gerir",
            "leite": "leite",
            "norma": "norma",
            "tosco": "tosco",
            "lenda": "lenda",
            "alude": "alude",
            "brava": "brava",
            "epoca": "época",
            "sinha": "sinhá",
            "rapaz": "rapaz",
            "tenso": "tenso",
            "parte": "parte",
            "campo": "campo",
            "exame": "exame",
            "aviao": "avião",
            "idolo": "ídolo",
            "psico": "psico",
            "arcar": "arcar",
            "reino": "reino",
            "tirar": "tirar",
            "venal": "venal",
            "malta": "malta",
            "soldo": "soldo",
            "praga": "praga",
            "agora": "agora",
            "vilao": "vilão",
            "quota": "quota",
            "anais": "anais",
            "corpo": "corpo",
            "aonde": "aonde",
            "sumir": "sumir",
            "indio": "índio",
            "virao": "virão",
            "risco": "risco",
            "praia": "praia",
            "logro": "logro",
            "antes": "antes",
            "preto": "preto",
            "traga": "traga",
            "fixar": "fixar",
            "voraz": "voraz",
            "pompa": "pompa",
            "cheio": "cheio",
            "exijo": "exijo",
            "quase": "quase",
            "filho": "filho",
            "certa": "certa",
            "texto": "texto",
            "turba": "turba",
            "nodoa": "nódoa",
            "oasis": "oásis",
            "copia": "cópia",
            "solto": "solto",
            "alado": "alado",
            "apego": "apego",
            "turva": "turva",
            "caixa": "caixa",
            "prova": "prova",
            "estao": "estão",
            "acesa": "acesa",
            "messe": "messe",
            "grave": "grave",
            "doido": "doído",
            "nivel": "nível",
            "ligar": "ligar",
            "perda": "perda",
            "parva": "parva",
            "verve": "verve",
            "conta": "conta",
            "apelo": "apelo",
            "verbo": "verbo",
            "atrio": "átrio",
            "tocar": "tocar",
            "aurea": "áurea",
            "pardo": "pardo",
            "lindo": "lindo",
            "trupe": "trupe",
            "coito": "coito",
            "fenda": "fenda",
            "livre": "livre",
            "dessa": "dessa",
            "sabia": "sabia",
            "opaco": "opaco",
            "alcar": "alçar",
            "navio": "navio",
            "viria": "viria",
            "fraco": "fraco",
            "retem": "retém",
            "afora": "afora",
            "festa": "festa",
            "jirau": "jirau",
            "ficha": "ficha",
            "etico": "ético",
            "astro": "astro",
            "parca": "parca",
            "faixa": "faixa",
            "elite": "elite",
            "oxala": "oxalá",
            "supra": "supra",
            "lidar": "lidar",
            "glosa": "glosa",
            "autor": "autor",
            "mente": "mente",
            "fatos": "fatos",
            "tinha": "tinha",
            "firme": "firme",
            "verba": "verba",
            "magia": "magia",
            "cioso": "cioso",
            "fatal": "fatal",
            "grata": "grata",
            "bater": "bater",
            "calda": "calda",
            "reses": "reses",
            "pique": "pique",
            "cousa": "cousa",
            "junco": "junco",
            "prive": "privê",
            "deixa": "deixa",
            "salve": "salve",
            "irmao": "irmão",
            "pagao": "pagão",
            "macio": "macio",
            "molho": "molho",
            "douto": "douto",
            "atual": "atual",
            "abriu": "abriu",
            "bicho": "bicho",
            "light": "light",
            "supor": "supor",
            "posto": "posto",
            "torso": "torso",
            "turvo": "turvo",
            "asilo": "asilo",
            "igneo": "ígneo",
            "sexta": "sexta",
            "extra": "extra",
            "vezes": "vezes",
            "orfao": "órfão",
            "judeu": "judeu",
            "sarca": "sarça",
            "curso": "curso",
            "caber": "caber",
            "longe": "longe",
            "rouca": "rouca",
            "locus": "locus",
            "besta": "besta",
            "porta": "porta",
            "pisar": "pisar",
            "drops": "drops",
            "canon": "cânon",
            "radio": "rádio",
            "desta": "desta",
            "abuso": "abuso",
            "ruina": "ruína",
            "zelar": "zelar",
            "video": "vídeo",
            "combo": "combo",
            "vosso": "vosso",
            "bioma": "bioma",
            "ereto": "ereto",
            "vinha": "vinha",
            "culpa": "culpa",
            "finda": "finda",
            "paira": "paira",
            "menos": "menos",
            "agudo": "agudo",
            "baixo": "baixo",
            "feudo": "feudo",
            "bonus": "bônus",
            "facto": "facto",
            "nosso": "nosso",
            "tetra": "tetra",
            "advir": "advir",
            "urgia": "urgia",
            "estio": "estio",
            "cutis": "cútis",
            "surja": "surja",
            "meigo": "meigo",
            "traco": "traço",
            "sitio": "sítio",
            "super": "super",
            "gosto": "gosto",
            "calao": "calão",
            "autos": "autos",
            "facho": "facho",
            "tento": "tento",
            "suave": "suave",
            "rumor": "rumor",
            "amena": "amena",
            "pilar": "pilar",
            "cocho": "cocho",
            "turma": "turma",
            "museu": "museu",
            "clean": "clean",
            "chama": "chama",
            "lasso": "lasso",
            "acoes": "ações",
            "geral": "geral",
            "acola": "acolá",
            "lapis": "lápis",
            "pifia": "pífia",
            "optar": "optar",
            "local": "local",
            "podio": "pódio",
            "boato": "boato",
            "mosto": "mosto",
            "hobby": "hobby",
            "medir": "medir",
            "julia": "júlia",
            "rubro": "rubro",
            "crime": "crime",
            "pacto": "pacto",
            "penta": "penta",
            "letal": "letal",
            "folga": "folga",
            "refem": "refém",
            "ponha": "ponha",
            "brabo": "brabo",
            "poema": "poema",
            "drama": "drama",
            "pareo": "páreo",
            "cacho": "cacho",
            "aluno": "aluno",
            "movel": "móvel",
            "aroma": "aroma",
            "mesma": "mesma",
            "vigia": "vigia",
            "cover": "cover",
            "feroz": "feroz",
            "hoste": "hoste",
            "vetar": "vetar",
            "peito": "peito",
            "pasmo": "pasmo",
            "fazia": "fazia",
            "rival": "rival",
            "acude": "açude",
            "metie": "metiê",
            "golpe": "golpe",
            "monte": "monte",
            "avida": "ávida",
            "finjo": "finjo",
            "axila": "axila",
            "coral": "coral",
            "teste": "teste",
            "chato": "chato",
            "ecoar": "ecoar",
            "forum": "fórum",
            "licao": "lição",
            "daqui": "daqui",
            "riste": "riste",
            "piada": "piada",
            "forem": "forem",
            "plebe": "plebe",
            "poeta": "poeta",
            "verde": "verde",
            "monge": "monge",
            "lesse": "lesse",
            "artur": "artur",
            "clima": "clima",
            "carta": "carta",
            "sucia": "súcia",
            "passa": "passa",
            "cetro": "cetro",
            "ebano": "ébano",
            "escol": "escol",
            "tacha": "tacha",
            "swing": "swing",
            "macro": "macro",
            "ateia": "ateia",
            "broxa": "broxa",
            "venha": "venha",
            "falha": "falha",
            "briga": "briga",
            "calmo": "calmo",
            "roupa": "roupa",
            "conto": "conto",
            "sarau": "sarau",
            "viram": "viram",
            "busca": "busca",
            "cargo": "cargo",
            "idoso": "idoso",
            "fruto": "fruto",
            "plaga": "plaga",
            "farta": "farta",
            "tarde": "tarde",
            "legua": "légua",
            "perco": "perco",
            "atimo": "átimo",
            "tribo": "tribo",
            "aviso": "aviso",
            "plumo": "plumo",
            "berro": "berro",
            "chefe": "chefe",
            "vento": "vento",
            "grama": "grama",
            "virar": "virar",
            "civil": "civil",
            "corso": "corso",
            "catre": "catre",
            "arado": "arado",
            "surto": "surto",
            "seixo": "seixo",
            "assar": "assar",
            "estro": "estro",
            "saldo": "saldo",
            "traje": "traje",
            "ornar": "ornar",
            "bruta": "bruta",
            "nuvem": "nuvem",
            "recem": "recém",
            "beijo": "beijo",
            "pedra": "pedra",
            "manga": "manga",
            "deste": "deste",
            "fosso": "fosso",
            "troca": "troca",
            "unica": "única",
            "giria": "gíria",
            "casar": "casar",
            "trato": "trato",
            "impia": "ímpia",
            "depor": "depor",
            "benca": "bença",
            "vedar": "vedar",
            "amiga": "amiga",
            "uteis": "úteis",
            "porte": "porte",
            "arfar": "arfar",
            "ticao": "tição",
            "deram": "deram",
            "magna": "magna",
            "irado": "irado",
            "ambar": "âmbar",
            "canso": "canso",
            "grota": "grota",
            "amado": "amado",
            "tutor": "tutor",
            "sosia": "sósia",
            "cifra": "cifra",
            "silvo": "silvo",
            "bazar": "bazar",
            "gabar": "gabar",
            "tiver": "tiver",
            "vazao": "vazão",
            "itens": "itens",
            "pasma": "pasma",
            "rural": "rural",
            "bruto": "bruto",
            "renda": "renda",
            "laudo": "laudo",
            "perto": "perto",
            "jejum": "jejum",
            "pavor": "pavor",
            "regio": "régio",
            "midia": "mídia",
            "segar": "segar",
            "bucho": "bucho",
            "nesse": "nesse",
            "pinho": "pinho",
            "tchau": "tchau",
            "inter": "inter",
            "feita": "feita",
            "minar": "minar",
            "orgao": "órgão",
            "odiar": "odiar",
            "vagar": "vagar",
            "fossa": "fossa",
            "viado": "viado",
            "molde": "molde",
            "areia": "areia",
            "clero": "clero",
            "vadio": "vadio",
            "lesto": "lesto",
            "meche": "meche",
            "sotao": "sótão",
            "pomar": "pomar",
            "aviar": "aviar",
            "negar": "negar",
            "canto": "canto",
            "mamae": "mamãe",
            "cenho": "cenho",
            "lesao": "lesão",
            "cinto": "cinto",
            "largo": "largo",
            "rocha": "rocha",
            "paiol": "paiol",
            "horto": "horto",
            "visto": "visto",
            "ileso": "ileso",
            "bolsa": "bolsa",
            "proto": "proto",
            "ruido": "ruído",
            "stand": "stand",
            "amada": "amada",
            "pugna": "pugna",
            "guria": "guria",
            "inves": "invés",
            "densa": "densa",
            "marca": "marca",
            "podar": "podar",
            "morfo": "morfo",
            "close": "close",
            "bunda": "bunda",
            "urdir": "urdir",
            "jogar": "jogar",
            "vista": "vista",
            "ufano": "ufano",
            "xucro": "xucro",
            "vasta": "vasta",
            "dubia": "dúbia",
            "mocho": "mocho",
            "frota": "frota",
            "chula": "chula",
            "civel": "cível",
            "penso": "penso",
            "cheia": "cheia",
            "bulir": "bulir",
            "umido": "úmido",
            "piche": "piche",
            "culta": "culta",
            "linha": "linha",
            "ubere": "úbere",
            "peita": "peita",
            "esgar": "esgar",
            "varoa": "varoa",
            "resto": "resto",
            "apear": "apear",
            "canil": "canil",
            "misto": "misto",
            "manto": "manto",
            "fundo": "fundo",
            "natal": "natal",
            "tenha": "tenha",
            "agape": "ágape",
            "demao": "demão",
            "monta": "monta",
            "narco": "narco",
            "fazes": "fazes",
            "santo": "santo",
            "nessa": "nessa",
            "findo": "findo",
            "barao": "barão",
            "campa": "campa",
            "cerca": "cerca",
            "volta": "volta",
            "gemer": "gemer",
            "simio": "símio",
            "jazer": "jazer",
            "velha": "velha",
            "chaga": "chaga",
            "album": "álbum",
            "preco": "preço",
            "logos": "logos",
            "polis": "pólis",
            "mover": "mover",
            "retro": "retro",
            "verao": "verão",
            "ardis": "ardis",
            "labia": "lábia",
            "letra": "letra",
            "cosmo": "cosmo",
            "seiva": "seiva",
            "ferpa": "ferpa",
            "venho": "venho",
            "folia": "folia",
            "banto": "banto",
            "matar": "matar",
            "punha": "punha",
            "alamo": "álamo",
            "nesta": "nesta",
            "etapa": "etapa",
            "sabor": "sabor",
            "porca": "porca",
            "audio": "áudio",
            "ceita": "ceita",
            "trago": "trago",
            "barro": "barro",
            "coroa": "coroa",
            "calca": "calça",
            "rente": "rente",
            "sigla": "sigla",
            "axial": "axial",
            "final": "final",
            "louro": "louro",
            "salva": "salva",
            "redor": "redor",
            "firma": "firma",
            "arroz": "arroz",
            "limpo": "limpo",
            "bolso": "bolso",
            "torna": "torna",
            "coevo": "coevo",
            "tumba": "tumba",
            "queda": "queda",
            "solta": "solta",
            "miope": "míope",
            "enjoo": "enjoo",
            "lutar": "lutar",
            "farol": "farol",
            "lousa": "lousa",
            "danca": "dança",
            "baixa": "baixa",
            "folha": "folha",
            "fugiu": "fugiu",
            "ousar": "ousar",
            "mimar": "mimar",
            "neste": "neste",
            "corar": "corar",
            "veloz": "veloz",
            "zumbi": "zumbi",
            "burra": "burra",
            "sinta": "sinta",
            "nacar": "nácar",
            "longo": "longo",
            "obtem": "obtém",
            "reler": "reler",
            "salmo": "salmo",
            "macho": "macho",
            "cacto": "cacto",
            "forro": "forro",
            "penca": "penca",
            "vazia": "vazia",
            "fatuo": "fátuo",
            "calor": "calor",
            "justa": "justa",
            "vario": "vário",
            "farto": "farto",
            "todas": "todas",
            "bedel": "bedel",
            "quite": "quite",
            "mania": "mania",
            "gueto": "gueto",
            "chave": "chave",
            "lucro": "lucro",
            "sugar": "sugar",
            "repor": "repor",
            "calvo": "calvo",
            "puido": "puído",
            "merda": "merda",
            "logia": "logia",
            "sexto": "sexto",
            "staff": "staff",
            "ultra": "ultra",
            "custo": "custo",
            "subir": "subir",
            "passe": "passe",
            "refil": "refil",
            "urgir": "urgir",
            "viger": "viger",
            "sadio": "sadio",
            "mimos": "mimos",
            "versa": "versa",
            "harem": "harém",
            "valer": "valer",
            "hifen": "hífen",
            "lento": "lento",
            "usual": "usual",
            "redea": "rédea",
            "socio": "sócio",
            "cardo": "cardo",
            "ardua": "árdua",
            "louca": "louca"
          }
        ]
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
.conteudo {
  margin: 80px;
  float: right;
}

.margin10 {
  margin-right: 10px;
}

</style>
