<!-- Script JS -->
<script>
    let selectedImage = null
    let magnitudes = [25, 50, 75, 100]; // array de magnitudes
    let imagenes = ['./images/copo.png', './images/menta.png', './images/flor.png', './images/dom.png']; // array de imágenes

    function mostrarImagen (i) {
        selectedImage = i
        console.log("index de img seleccionada", selectedImage)
    }

</script>

<!-- Estructura contenido HTML -->
<div class="container">
    <h1 class="titulo">¿QUÉ TANTA AGUA CONSUMIMOS EN EL AÑO?</h1>
    <h2 class="subtitulo">Seleccioná una estación y descubrilo</h2>
        <div class="buttons">
            {#each ["", "", "", ""] as button, i}
                <button on:click={() => mostrarImagen(i)}>
                    <img src={imagenes[i]} alt={button} style="width: 50px;" /> <!-- Assign image to button as an icon with a width of 50px -->
                    {button}
                </button>
            {/each}
            
        </div>

       

    <div class="col-container">
        {#each magnitudes as m, i}
        <div class="col-wrap" class:show-mask={selectedImage === i}>
            <div class = 'column' style='height: {m*4}px' ></div>
            <img class='mask' src="./images/tipo.png" alt="" style="display: {selectedImage === i ? 'block' : 'none'};">
        </div>

        {/each}
    </div>
</div>    



<!-- Estilos CSS -->
<style>

    @import url('https://fonts.googleapis.com/css2?family=Archivo+Black&display=swap');

    .container{
        display: flex;
        flex-direction: column;
    
    }
    .titulo{
        margin-top: 35px;
        font-family: "Archivo Black", sans-serif;
        font-weight: bold;
        /*text-decoration: underline;*/
        text-align: center;
        color: blue;
    }

    .subtitulo{
        margin-top: 15px;
        font-family: "Archivo Black", sans-serif;
        font-weight: bold;
        background-color: blue;
        /*text-decoration: underline;*/
        text-align: center;
        color: white;
    }

    .buttons{
        margin-top: 15px;
        display: flex;
        justify-content: center;
        margin-bottom: 300px;
    }
    .col-container{  
        display: flex;
        align-items: flex-end;
        justify-content:center;
    }
    .column{
        background-color: rgb(0, 0, 255);
        /*background-image: url('./images/agua.png');*/
        width: 200px;   
    }
    .mask{
        width: 200px;
        height:400px; 
        position: absolute;
        bottom: 0;
        z-index: 1;
    }
    .show-mask {
        display: block !important;
    }
    .col-wrap{
        margin: -150px;
        position: absolute;
        width: 100px;
        display: none;
    }
</style>