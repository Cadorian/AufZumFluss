<template>
  <div id="app">
    <div id="left-panel" style="float: left;">
      <center>
		<div id="shovelWrapper"><div class="spaceholder" /></div>
		<div id="shovelCnt" style="display:none;">
         <div id="dragShovel3"><div id="dragShovel" v-for="(shovel, index) in shovels3" :key="index">
          <img
            src="./assets/schaufel.png"
            v-if="shovel"
			
			ondragstart="window.vm.dragOrTouchStart(event)"
			ondragend="window.vm.dragEnd(event)"
			ontouchstart="window.vm.dragOrTouchStart(event)"
            ontouchmove="window.vm.handleTouchMoving(event)"
			ontouchend="window.vm.touchEnd(event)"
			
          ><br />
        </div></div>
		<div id="dragShovel2"><div id="dragShovel" v-for="(shovel, index) in shovels2" :key="index">
          <img
            src="./assets/schaufel.png"
            ondragstart="window.vm.dragOrTouchStart(event)"
			ondragend="window.vm.dragEnd(event)"
			ontouchstart="window.vm.dragOrTouchStart(event)"
            ontouchmove="window.vm.handleTouchMoving(event)"
			ontouchend="window.vm.touchEnd(event)"
            v-if="shovel"
          ><br />
        </div><br /><div class="spaceholderShovel"></div><br /></div></div>
        <img id="controller-button" src="./assets/play.png" v-on:click="playHandler">
        <img id="controller-button" src="./assets/stop.png" v-on:click="reset" style="margin-left: 2%">
		<br>
		<img id="controller-button" src="./assets/levelDown.png" v-on:click="levelDownHandler">
		<img id="level" src="./assets/level.png" style="margin-left: 5%">
        <img id="controller-button" src="./assets/levelUp.png" v-on:click="levelUpHandler" style="margin-left: 5%">
        <br>
      </center>
    </div>

    <div id="crocoWater">
      <img src="./assets/croco_wasser.png">
    </div>
	<div id="playground">
	</div>
	
	<div id="levels" style="display:none;">
		<div id="playground0">
		  <table>
			<tr v-for="(row, index) in leveldaten[0][0]" :key="index">
			  <th v-for="(type, index) in row" :key="index" ref="fieldslot">
				<img src="./assets/croco.png" v-if="type==0">
				<img src="./assets/schmutz.png" ondrop="window.vm.handleDrop(event)" ondragover="event.preventDefault();" v-if="type==1">
				<img src="./assets/fels.png" v-if="type==2">
				<img src="./assets/ziel.png" v-if="type==3">
				<div class="empty" v-if="type==4"/>
			  </th>
			</tr>
		  </table>
		</div>
		<div id="playground1">
		  <table>
			<tr v-for="(row, index) in leveldaten[1][0]" :key="index">
			  <th v-for="(type, index) in row" :key="index" ref="fieldslot">
				<img src="./assets/croco.png" v-if="type==0">
				<img src="./assets/schmutz.png" ondrop="window.vm.handleDrop(event)" ondragover="event.preventDefault();" v-if="type==1">
				<img src="./assets/fels.png" v-if="type==2">
				<img src="./assets/ziel.png" v-if="type==3">
				<div class="empty" v-if="type==4"/>
			  </th>
			</tr>
		  </table>
		</div>
		<div id="playground2">
		  <table>
			<tr v-for="(row, index) in leveldaten[2][0]" :key="index">
			  <th v-for="(type, index) in row" :key="index" ref="fieldslot">
				<img src="./assets/croco.png" v-if="type==0">
				<img src="./assets/schmutz.png" ondrop="window.vm.handleDrop(event)" ondragover="event.preventDefault();" v-if="type==1">
				<img src="./assets/fels.png" v-if="type==2">
				<img src="./assets/ziel.png" v-if="type==3">
				<div class="empty" v-if="type==4"/>
			  </th>
			</tr>
		  </table>
		</div>
		<div id="playground3">
		  <table>
			<tr v-for="(row, index) in leveldaten[3][0]" :key="index">
			  <th v-for="(type, index) in row" :key="index" ref="fieldslot">
				<img src="./assets/croco.png" v-if="type==0">
				<img src="./assets/schmutz.png" ondrop="window.vm.handleDrop(event)" ondragover="event.preventDefault();" v-if="type==1">
				<img src="./assets/fels.png" v-if="type==2">
				<img src="./assets/ziel.png" v-if="type==3">
				<div class="empty" v-if="type==4"/>
			  </th>
			</tr>
		  </table>
		</div>
		<div id="playground4">
		  <table>
			<tr v-for="(row, index) in leveldaten[4][0]" :key="index">
			  <th v-for="(type, index) in row" :key="index" ref="fieldslot">
				<img src="./assets/croco.png" v-if="type==0">
				<img src="./assets/schmutz.png" ondrop="window.vm.handleDrop(event)" ondragover="event.preventDefault();" v-if="type==1">
				<img src="./assets/fels.png" v-if="type==2">
				<img src="./assets/ziel.png" v-if="type==3">
				<div class="empty" v-if="type==4"/>
			  </th>
			</tr>
		  </table>
		</div>
		<div id="playground5">
		  <table>
			<tr v-for="(row, index) in leveldaten[5][0]" :key="index">
			  <th v-for="(type, index) in row" :key="index" ref="fieldslot">
				<img src="./assets/croco.png" v-if="type==0">
				<img src="./assets/schmutz.png" ondrop="window.vm.handleDrop(event)" ondragover="event.preventDefault();" v-if="type==1">
				<img src="./assets/fels.png" v-if="type==2">
				<img src="./assets/ziel.png" v-if="type==3">
				<div class="empty" v-if="type==4"/>
			  </th>
			</tr>
		  </table>
		</div>
		<div id="playground6">
		  <table>
			<tr v-for="(row, index) in leveldaten[6][0]" :key="index">
			  <th v-for="(type, index) in row" :key="index" ref="fieldslot">
				<img src="./assets/croco.png" v-if="type==0">
				<img src="./assets/schmutz.png" ondrop="window.vm.handleDrop(event)" ondragover="event.preventDefault();" v-if="type==1">
				<img src="./assets/fels.png" v-if="type==2">
				<img src="./assets/ziel.png" v-if="type==3">
				<div class="empty" v-if="type==4"/>
			  </th>
			</tr>
		  </table>
		</div>
		<div id="playground7">
		  <table>
			<tr v-for="(row, index) in leveldaten[7][0]" :key="index">
			  <th v-for="(type, index) in row" :key="index" ref="fieldslot">
				<img src="./assets/croco.png" v-if="type==0">
				<img src="./assets/schmutz.png" ondrop="window.vm.handleDrop(event)" ondragover="event.preventDefault();" v-if="type==1">
				<img src="./assets/fels.png" v-if="type==2">
				<img src="./assets/ziel.png" v-if="type==3">
				<div class="empty" v-if="type==4"/>
			  </th>
			</tr>
		  </table>
		</div>
		<div id="playground8">
		  <table>
			<tr v-for="(row, index) in leveldaten[8][0]" :key="index">
			  <th v-for="(type, index) in row" :key="index" ref="fieldslot">
				<img src="./assets/croco.png" v-if="type==0">
				<img src="./assets/schmutz.png" ondrop="window.vm.handleDrop(event)" ondragover="event.preventDefault();" v-if="type==1">
				<img src="./assets/fels.png" v-if="type==2">
				<img src="./assets/ziel.png" v-if="type==3">
				<div class="empty" v-if="type==4"/>
			  </th>
			</tr>
		  </table>
		</div>
	</div>
	<div id="movingshovel" style="width:75px;height:75px;position:absolute;background:url('./dist/schaufel.png');display:none;" ></div>
  </div>
</template>

<script>
const CROCO = 0;
const STONE1 = 1;
const STONE2 = 2;
const GOAL = 3;
const EMPTY = 4;

export default {
  name: "app",
  mounted() {
	window.vm = this; // Variable fuer Vue-Instanz setzen, um auch in Event-Handlern darauf zugreifen zu koennen
	this.loadLevel(0);
  },
  data() {
    return {
	
	  // LEVELDATEN: Dimensionen -> 1: Level (0-8), 2: Infos [Playground [Row[Column]] | [shovels, groesse, start, ziel]] 
		leveldaten: [[[
		[STONE1, EMPTY, STONE1, GOAL],
        [STONE1, STONE1, EMPTY, STONE1],
        [EMPTY, STONE1, EMPTY, EMPTY],
        [CROCO, STONE1, STONE1, STONE1],
      ],[[true,true],4,12,3]],[[
		[STONE1, STONE1, GOAL, EMPTY],
        [STONE1, EMPTY, STONE2, STONE1],
        [EMPTY, STONE2, STONE2, EMPTY],
        [CROCO, EMPTY, STONE1, EMPTY],
	  ],[[true,true],4,12,2]],[[
		[STONE2, STONE1, STONE1, GOAL],
        [STONE1, EMPTY, STONE2, STONE2],
        [EMPTY, STONE1, EMPTY, STONE1],
        [STONE1, CROCO, STONE1, EMPTY],
      ],[[true,true,true],4,13,3]],[[
		[STONE1, EMPTY, EMPTY, GOAL],
        [EMPTY, STONE1, STONE2, STONE1],
        [STONE2, EMPTY, STONE1, STONE1],
        [STONE1, STONE1, CROCO, STONE2],
      ],[[true,true],4,14,3]],[[
		[EMPTY, EMPTY, EMPTY, STONE1, GOAL],
        [STONE2, EMPTY, STONE1, STONE2, EMPTY],
        [EMPTY, EMPTY, STONE2, EMPTY, STONE2],
        [STONE1, STONE1, EMPTY, EMPTY, STONE2],
        [CROCO, EMPTY, EMPTY, STONE1, STONE1]
      ],[[true,true],5,20,4]],[[
		[STONE2, STONE1, EMPTY, STONE1, GOAL],
        [EMPTY, EMPTY, STONE2, STONE2, STONE1],
        [STONE1, STONE1, EMPTY, STONE2, STONE1],
        [EMPTY, STONE2, STONE1, EMPTY, STONE1],
        [CROCO, EMPTY, STONE1, EMPTY, STONE2]
      ],[[true,true,true],5,20,4]],[[
		[STONE2, STONE2, STONE1, EMPTY, GOAL],
        [STONE1, STONE1, EMPTY, STONE1, STONE1],
        [EMPTY, EMPTY, STONE2, STONE2, STONE1],
        [STONE1, STONE1, STONE1, EMPTY, EMPTY],
        [CROCO, EMPTY, STONE2, STONE1, STONE2]
      ],[[true,true,true],5,20,4]],[[
		[STONE1, EMPTY, STONE2, STONE1, GOAL],
        [STONE1, STONE2, STONE1, EMPTY, STONE2],
        [EMPTY, STONE1, STONE1, EMPTY, EMPTY],
        [EMPTY, STONE1, STONE2, STONE1, STONE1],
        [CROCO, STONE1, EMPTY, STONE2, STONE2]
      ],[[true,true,true],5,20,4]],[[
        [STONE1, STONE1, GOAL, STONE1, EMPTY],
        [EMPTY, EMPTY, STONE2, STONE2, STONE1],
        [STONE2, EMPTY, STONE1, EMPTY, STONE1],
        [EMPTY, STONE1, STONE2, EMPTY, EMPTY],
        [STONE2, STONE2, CROCO, STONE1, STONE1]
      ],[[true,true,true],5,22,2]]],
	  
	  shovels3: [true,true,true],
	  shovels2: [true,true],
	
	  // aktuelle Levelinfos
	  level: 0,
      shovels: [true, true],
      playground: [],
	  groesse: 4,
	  playInProgress: false,
	  
	  // fuer Wegesuche
	  belegt: [1,0,1,0,1,1,0,1,0,1,0,0,0,1,1,1], // 0: leer, 1: belegt 
	  adjliste5: [
		[1,5],[0,2,6],[1,3,7],[2,4,8],[3,9],
		[0,6,10],[1,5,7,11],[2,6,8,12],[3,7,9,13],[4,8,14],
		[5,11,,15],[6,10,12,16],[7,11,13,17],[8,12,14,18],[9,13,19],
		[10,16,20],[11,15,17,21],[12,16,18,22],[13,17,19,23],[14,18,24],
		[15,21],[16,20,22],[17,21,23],[18,22,24],[19,23]
	  ],
	  adjliste4: [
		[1,4],[0,2,5],[1,3,6],[2,7],
		[0,5,8],[1,4,6,9],[2,5,7,10],[3,6,11],
		[4,9,12],[5,8,10,13],[6,9,11,14],[7,10,15],
		[8,13],[9,12,14],[10,13,15],[11,14]
	  ],
	  start: 12,
	  ziel: 3,
	  weg: [],
	  
	  // fuer Drag and Drop
	  draggedShovel: -1,
      touch: null
    };
  },
  methods: {
  
	dragOrTouchStart: function(e){
		window.vm.draggedShovel = 0;
		var elem = e.target.parentElement;
		while(elem.previousElementSibling != null){
		elem = elem.previousElementSibling;
		window.vm.draggedShovel++;
	  }
	},

	handleTouchMoving: function(e){
		window.vm.touch = e.targetTouches[0];
		e.target.style.display='none';
		document.getElementById('movingshovel').style.display='block';
		document.getElementById('movingshovel').style.left=window.vm.touch.pageX-38+"px";
		document.getElementById('movingshovel').style.top=window.vm.touch.pageY-38+"px";
	},

	dragEnd: function(e){
	  window.vm.draggedShovel = -1;
	},

	touchEnd: function(e){
		var shovelNo = window.vm.draggedShovel;
		e.target.style.display='';
		window.vm.draggedShovel = -1;
		document.getElementById('movingshovel').style.display='none';
		var targetElem = document.elementFromPoint(window.vm.touch.clientX,window.vm.touch.clientY);
		window.vm.shovelDroppedOverObj(shovelNo, targetElem);
	},
	
	handleDrop: function(e){
		var shovelNo = window.vm.draggedShovel;
		window.vm.draggedShovel = -1;
		var targetElem = e.target;
		e.preventDefault();
		window.vm.shovelDroppedOverObj(shovelNo, targetElem);
	},
	
	shovelDroppedOverObj:function(shovelNo, targetElem){
		if(shovelNo < 0) return;
		
		//is it a removable obj?
		if(targetElem.tagName.toUpperCase() == "IMG"){
			targetElem = targetElem.parentElement;
		}
		if(targetElem.tagName.toUpperCase() != "TH" && targetElem.tagName.toUpperCase() != "TD") return;
		
		var colum = 0;
		var elem = targetElem;
		while(elem.previousElementSibling != null){
			elem = elem.previousElementSibling;
			colum++;
		}
		var row = 0;
		elem = elem.parentElement;
		while(elem.previousElementSibling != null){
			elem = elem.previousElementSibling;
			row++;
		}
		if(elem.parentElement.parentElement != document.getElementById('playground') && elem.parentElement.parentElement.parentElement != document.getElementById('playground')) return;

		if (window.vm.playground[row][colum] != STONE1) return;
		window.vm.playground[row][colum] = EMPTY;
		var indexBelegt;
		if(window.vm.groesse == 4){
			indexBelegt = row*4+colum;
		}else{
			indexBelegt = row*5+colum;
		}
		window.vm.belegt[indexBelegt] = 0;
		targetElem.innerHTML = "";
		document.getElementById("left-panel").children[0].children[0].children[shovelNo].children[0].style.display="none";
	},
    
	playHandler: function(ev) {
		if(!window.vm.playInProgress){
			window.vm.playInProgress = true;
			var geschafft = window.vm.wegeSuche();
			if(geschafft == false){
				alert("Der Weg ist nicht frei.");
				window.vm.playInProgress = false;
			}else{
				window.vm.laufen();
			}
		}
	},
	
	targetReachedHandler: function(){
		if(window.vm.level < 8){ // Level: 0-8
			alert("Gewonnen!\nAuf zum nächsten Level!");
			var levelNew = window.vm.level + 1;
			window.vm.loadLevel(levelNew);
		}else{
			alert("Alle Level geschafft!");
		}
		window.vm.playInProgress = false;
	},
	
	reset: function(ev) {
		window.vm.loadLevel(window.vm.level);
	},
	
	levelDownHandler: function(ev) {
		if(window.vm.level > 0){
			window.vm.loadLevel(window.vm.level-1);
		}
	},
	
	levelUpHandler: function(ev) {
		if(window.vm.level < 8){
			window.vm.loadLevel(window.vm.level+1);
		}
	},
	
	wegeSuche: function(){ 
		//dijkstra algorithmus
		var anzahl = window.vm.groesse;
		var vorgaenger = new Array(anzahl*anzahl);
		var distanz = [];
		for(let i=0; i<anzahl*anzahl; i++){
			distanz.push(1000);
		}
		distanz[window.vm.start] = 0;
		var unbesucht = new Array();
		unbesucht.push(window.vm.start);
		var unbesuchtEingefuegt = new Array(anzahl);
		for(let i=0; i<anzahl*anzahl; i++){
			unbesuchtEingefuegt[i] = false;
		}
		unbesuchtEingefuegt[window.vm.start] = true;
		
		// richtige adjazenzliste auswaelen
		var adjlis;
		if(window.vm.groesse == 4){
			adjlis = window.vm.adjliste4;
		}else{
			adjlis = window.vm.adjliste5;
		}
		
		while(unbesucht.length != 0){
			var min = window.vm.minimumArray(distanz,unbesucht);
			unbesucht.splice(unbesucht.indexOf(min),1);
			for(let c of adjlis[min]){ // alle vier Felder um das aktuelle Feld
				// erreichbare Nachbarn in unbesucht einfuegen, wenn sie nicht darin sind und auch noch nicht waren
				if(window.vm.belegt[c] == 0 && unbesucht.includes(c) == false && unbesuchtEingefuegt[c] == false){
					unbesucht.push(c);
					unbesuchtEingefuegt[c] = true;
				}
				// ueberpruefen ob c unbelegt und unbesucht
				if(window.vm.belegt[c] == 0 && unbesucht.includes(c)){
					//Distanz aktualisieren und Vorgaenger festlegen
					var disNeu = distanz[min] + 1;
					if(disNeu < distanz[c]){
						distanz[c] = disNeu;
					}
					vorgaenger[c] = min;
				}
			}
		}
		
		//Weg gefunden?
		if(distanz[window.vm.ziel] == 1000){
			//nicht erfolgreich
			return false;
		}else{
			//Weg von hinten herausfinden und im Array weg die Indizies auflisten
			var fertig = false;
			var aktIndex = window.vm.ziel;
			window.vm.weg.unshift(window.vm.ziel);
			while(fertig == false){
				var vorAkt = vorgaenger[aktIndex];
				if(vorAkt == window.vm.start){
					fertig = true;
				}else{
					window.vm.weg.unshift(vorAkt);
					aktIndex = vorAkt;
				}
			}
			return true;
		}
	},
	
	minimumArray: function(distanz,unbesucht){
		var min = 1000; 
		var minIndex = -1;
		for(let i of unbesucht){
			if(distanz[i] < min){
				min = distanz[i];
				minIndex = i;
			}
		}
		return minIndex;
	},
	
	getIndexTableRow: function(i){
		var row = Math.floor(i / window.vm.groesse);
		return row;
	},
	
	getIndexTableCol: function(i){
		var column =  i % window.vm.groesse;
		return column;
	},
	
	laufen: function(aktIndex){
		if(aktIndex==undefined) {
			aktIndex = window.vm.start;
			}
		if(window.vm.weg.length == 0) return;
		var tableRow = window.vm.getIndexTableRow(aktIndex);
		var tableCol = window.vm.getIndexTableCol(aktIndex);
		var next = window.vm.weg.shift(); 
		var tableRowNew = window.vm.getIndexTableRow(next);
		var tableColNew = window.vm.getIndexTableCol(next);
		//Croco an aktueller Stelle entfernen und an neuer einfuegen
		window.vm.playground[tableRow][tableCol] = EMPTY;
		window.vm.playground[tableRowNew][tableColNew] = CROCO;
		window.vm.setCrocoInTable(tableRowNew,tableColNew, true);
		window.vm.setCrocoInTable(tableRow,tableCol, false);
		
		if(window.vm.weg.length != 0){
			setTimeout("window.vm.laufen("+next+")", 500);	
		}else{
			setTimeout("window.vm.targetReachedHandler()", 10);
		}
	},
	
	setCrocoInTable: function(row, colum, isCroco){
		var tbody=document.getElementById("playground").children[0].children[0];
		var trParent;
		if(tbody.tagName.toUpperCase() == "TBODY"){
			trParent = tbody;
		}else{
			trParent = tbody.parentElement;
		}
		if(isCroco){
			trParent.children[row].children[colum].innerHTML = "<img src='./dist/croco.png' />";
		}else{
			trParent.children[row].children[colum].innerHTML = "<div class='empty'></div>";
		}
	},
	
    loadLevel: function(levelNo) {	
		// Variablen neu setzen bzw. reseten
		window.vm.level = levelNo;
		window.vm.shovels = window.vm.leveldaten[levelNo][1][0];
		window.vm.groesse = window.vm.leveldaten[levelNo][1][1];
		window.vm.start = window.vm.leveldaten[levelNo][1][2];
		window.vm.ziel = window.vm.leveldaten[levelNo][1][3];
		window.vm.weg = [];
		window.vm.draggedShovel = -1;
		window.vm.touch = null;
		window.vm.playInProgress = false;
		// Playground & Shovels HTML aktualisieren aus Leveldaten
		document.getElementById('playground').innerHTML = document.getElementById('playground'+levelNo).innerHTML;
		if(window.vm.shovels.length == 2){
			document.getElementById('shovelWrapper').innerHTML = document.getElementById('dragShovel2').innerHTML;
		}else{
			document.getElementById('shovelWrapper').innerHTML = document.getElementById('dragShovel3').innerHTML;
		}
		// Playground-Array neu initialisieren und Inhalt aus Leveldaten kopieren
		window.vm.playground = new Array(window.vm.groesse);
		for(let i=0; i<window.vm.playground.length; i++){
			window.vm.playground[i] = new Array(window.vm.groesse);
		}
		for(let i=0; i<window.vm.playground.length; i++){
			for(let j=0; j<window.vm.playground[i].length; j++){
				window.vm.playground[i][j] = window.vm.leveldaten[levelNo][0][i][j];
			}
		}	
		// belegt-Array neu fuellen
		window.vm.belegt = new Array(window.vm.groesse * window.vm.groesse);
		let cnt = 0;
		for(let i=0; i<window.vm.playground.length; i++){
			for(let j=0; j<window.vm.playground[i].length; j++){
				if(window.vm.playground[i][j] == STONE1 || window.vm.playground[i][j] == STONE2){
					window.vm.belegt[cnt] = 1;
				}else{
					window.vm.belegt[cnt] = 0;
				}
				cnt++;
			}
		}
	}
  }
};

</script>

<style lang="scss">
body {
  background:url(./assets/sumpf_hg.jpg) grey no-repeat;
  background-size: cover;
  min-width:810px;
}

th,
td {
  border: 1px solid #716b61;
}

table {
  height: 100%;
  width: 100%;
}

.empty {
  height: 54px;
  width: 75px;
}

.spaceholder{
	width: 75px;
	height: 225px;
}

.spaceholderShovel{
	width: 75px;
	height: 74px;
}

#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

#left-panel {
  background-color: #736f6d;
  width:25%;
  min-width:290px;
  position: relative;
  height: 100%;
  padding: 1%;
  border: 2px solid #666260;
  /*	box-shadow: 5px 5px rgba(0,0,0,0.5); */
}
@media (max-width: 850px) {
	#left-panel {
		max-width:210px;
	}
}

#crocoWater {
  float: right;
  margin-right: 5%;
  margin-top: -50px;
  height: 120px;
}

#playground {
  background-color: #c7c3b9;
  width: 50%;
  position: relative;
  height: 390px;
  border: 2px solid #716b61;
  float: left;
  margin-left: 12%;
}

#controller-button {
  border: 2px solid transparent;
  &:hover {
    border: 2px solid #666260;
  }
}

#level {
	border: 2px solid transparent;
}

#dragShovel {
  border: 2px solid transparent;
  width: 75px;
  height: 75px;
  padding: 1em;

  &:hover {
    border: 2px solid #666260;
  }
}

</style>
