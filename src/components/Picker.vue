
<template>
     <div id="app" class="container">
        <div class="row">
            <div class="col-6">
                <div class="col-12">
                        <h3>Veuillez saisir un chiffre entre 1 et 255 :</h3>
                    <hr />
                    <div class="form-group">
                        <label>Vert :</label>
                        <input class="form-control" v-model="green" type="number" />
                    </div>
                    <hr />
                    <div class="form-group">
                        <label>Bleu :</label>
                        <input class="form-control" v-model="blue" type="number" />
                    </div>
                    <hr />
                    <div class="form-group">
                        <label>Rouge :</label>
                        <input class="form-control" v-model="red" type="number" />
                    </div>
                    <hr />
                    <div class="col-12">
                        <button class="btn-primary" @click="saveSquare()">Sauvegarder</button>
                        <button class="btn-danger" @click="reset()">Annuler</button>
                    </div>
                    <hr />
                        <h3>Nombre de carrés  : {{ nbrOfSquares }} </h3>
                    <hr />
                    <div class="col-12" v-if="nbrOfSquares">
                        <div class="prevsquare" v-for="square in squares" :key="square.id"  @click="selectedSquare=square" :style="{ backgroundColor: square }" ></div>
                    </div>
                    <h3 v-else >Ajouter des couleurs !</h3>
                </div>
            </div>
            <div class="col-6">
                <div class="square mx-auto" :style="{ backgroundColor: selectedSquare }"></div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
  name: 'Picker',
  data() {
    return {
            green: 0,
            blue: 0,
            red: 0,
            squares: [],
            selectedSquare:''
            }
          },
    methods : {
                resetColor() {
                    this.red = 0;
                    this.green = 0;
                    this.blue = 0;
                },
                saveSquare () {
                   this.squares.push(`rgb(${ this.red },${ this.green },${ this.blue} )`);
                   this.resetColor();
                   
               },
               reset() {
                    this.squares = [];
                    this.resetColor();
               }
            },
    computed: {
            nbrOfSquares() {
                return this.squares.length
                }
              }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
.square {
    width: 300px;
    height: 300px;
    margin-top: 50px;
    background-color: #ddd;
}

.prevsquare {
    width: 50px;
    height: 50px;
    display: inline-block;
    margin-left: 10px;
    margin-top: 10px;
    cursor: pointer; 
}
</style>
