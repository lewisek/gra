<html>
<head>
				<body>
				<div id="div1"></div>
				<script>
		 
				var ile=59;
				
				function stoper()
				{
				godzin =Math.floor(ile/3600);
				minut =Math.floor(ile/60)%60;
				sekund =ile%60;
				

				document.getElementById('div1').innerHTML = ' Pozostało:  0'+minut+':'+sekund+' ';
				
				ile--;
					if(ile<0)
					{
					clearInterval(intervalHandler);
					}
					if(ile<0)
					{
						alert("Koniec czasu")
					}
					
				
				}
				
				var intervalHandler=setInterval(stoper,1000);
				</script>
				</body>


<style>
#div1 {
    witth: 100%;
    text-align: center;
    color: red;
    font-size: 30px;
}

div#memory_board{
	background:rgb(0, 0, 0);
	border:rgb(255, 0, 0) 1px solid;
	width:800px;
	height:540px;
	padding:24px;
	margin:0px auto;
}

div#memory_board > div{
	background: url(tile_bg.jpg) no-repeat;
	border:rgb(255, 255, 255) 1px solid;
	width:71px;
	height:71px;
	float:left;
	margin:10px;
	padding:20px;
	font-size:64px;
	cursor:pointer;
	text-align:center;
}
</style>

<script>
class {
	constructor(memory_array) {
		this.memory_array = ['🔞','🔞','🤡','🤡','👾','👾','🚍','🚍','♿','♿','🚔','🚔','🤑','🤑','🎃','🎃','🕵️‍','🕵️‍','🚜','🚜','💩','💩','😎','😎'];
	}

	memory_tile_shuffle() {
		let i = this.memory_array.length;
		let j = null;
		let temp = null;
    while(--i > 0){
        j = Math.floor(Math.random() * (i+1));
        temp = this.memory_array[j];
        this.memory_array[j] = this.memory_array[i];
        this.memory_array[i] = temp;
    }
	}

}
var memory_array = ['🔞','🔞','🤡','🤡','👾','👾','🚍','🚍','♿','♿','🚔','🚔','🤑','🤑','🎃','🎃','🕵️‍','🕵️‍','🚜','🚜','💩','💩','😎','😎'];
var memory_values = [];
var memory_tile_ids = [];
var tiles_flipped = 0;
Array.prototype.memory_tile_shuffle = function(){
    var i = this.length, j, temp;
    while(--i > 0){
        j = Math.floor(Math.random() * (i+1));
        temp = this[j];
        this[j] = this[i];
        this[i] = temp;
    }
}
function newBoard(){
	tiles_flipped = 0;
	var output = '';
    memory_array.memory_tile_shuffle();
	for(var i = 0; i < memory_array.length; i++){
		output += '<div id="tile_'+i+'" onclick="memoryFlipTile(this,\''+memory_array[i]+'\')"></div>';
	}
	document.getElementById('memory_board').innerHTML = output;
}
function memoryFlipTile(tile,val){
	if(tile.innerHTML == "" && memory_values.length < 2){
		tile.style.background = '#FF0000';
		tile.innerHTML = val;
		if(memory_values.length == 0){
			memory_values.push(val);
			memory_tile_ids.push(tile.id);
		} else if(memory_values.length == 1){
			memory_values.push(val);
			memory_tile_ids.push(tile.id);
			if(memory_values[0] == memory_values[1]){
				tiles_flipped += 2;
				memory_values = [];
            	memory_tile_ids = [];
				if(tiles_flipped == memory_array.length){
					alert("🎊Gratulacje🎊, Wygrałeś Talon 💳");
					document.getElementById('memory_board').innerHTML = "";
					newBoard();
				}
			} else {
				function flip2Back(){

				    var tile_1 = document.getElementById(memory_tile_ids[0]);
				    var tile_2 = document.getElementById(memory_tile_ids[1]);
				    tile_1.style.background = 'url(tile_bg.jpg) no-repeat';
            	    tile_1.innerHTML = "";
				    tile_2.style.background = 'url(tile_bg.jpg) no-repeat';
            	    tile_2.innerHTML = "";
				    memory_values = [];
            	    memory_tile_ids = [];
				}
				setTimeout(flip2Back, 700);
			}
		}
	}
}
</script>
</head>
<body>
<div id="memory_board"></div>
<script>newBoard();</script>
</body>
</html>
