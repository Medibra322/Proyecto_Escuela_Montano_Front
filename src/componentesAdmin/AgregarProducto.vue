<template>
    <div class="formulario">
        <h1 class="py-4 text-center">Agregar Producto</h1>
        <form @submit.prevent="agregarProducto">
            <div class="form-group">
                <label>Imagen del Producto (URL):</label>
                <input type="text" v-model="photo">
            </div>
            <div class="form-group">
                <label>Imagen del Producto (Local):</label>
                <input type="file" @change="handleFileUpload" accept="image/*">
                <br />
                <img v-if="imagePreview" class="foto-previsualizacion" :src="imagePreview" alt="Vista previa de la imagen">
            </div>
            
            <label>Categoría del Producto:</label>
            <select v-model="categoria">
                <option value="car">Carniceria</option>
                <option value="pas">Pasteleria</option>
                <option value="pin">Pintxos</option>
                <option value="rac">Raciones</option>
            </select>
            <br />

            <label>Nombre del Producto:</label>
            <input type="text" v-model="nombre" />
            <br />

            <label>Precio del Producto:</label>
            <input type="text" v-model="precio" />
            <br />

            <button type="submit">Agregar</button>
        </form>
    </div>
</template>

<script setup>
import { ref } from 'vue';
import axios from "axios"; 

const categoria = ref('');
const nombre = ref('');
const precio = ref('');
const photo = ref(undefined);

const imagePreview = ref(null);

const agregarProducto = async () => {
    const photoValue = photo.value || imagePreview.value;
    const categoriaValue = categoria.value;
    const nombreValue = nombre.value;
    const precioValue = precio.value;

    // Limpia los campos
    categoria.value = '';
    nombre.value = '';
    precio.value = '';
    photo.value = undefined;

    try {
        const response = await axios.post('http://127.0.0.1:5000/add_producto', {
            img: photoValue,
            idcat: categoriaValue,
            nombre: nombreValue,
            precio: precioValue,
        });

        // Aquí puedes manejar la respuesta del servidor si es necesario
        console.log('Respuesta del servidor:', response.data);
    } catch (error) {
        // Manejo de errores
        console.error('Error al enviar la solicitud:', error);
    }
};

const handleFileUpload = (event) => {
    const file = event.target.files[0];
    if (file) {
        // Convierte el archivo a una URL de objeto
        const imageUrl = URL.createObjectURL(file);
        imagePreview.value = imageUrl;
    } else {
        imagePreview.value = null;
    }
};
</script>


<style>
/* Estilos para centrar el formulario */
.formulario {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;

}

form {
    width: 50vw;
    max-width: 400px;
    padding: 20px;
    border: 1px solid #ccc;
    border-radius: 5px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}

h2 {
    text-align: center;
    margin-bottom: 20px;
}

label {
    display: block;
    margin-bottom: 10px;
}

input,
select,
button {
    width: 100%;
    padding: 10px;
    margin-bottom: 15px;
    border: 1px solid #ccc;
    border-radius: 3px;
}

button {
    background-color: #4caf50;
    color: white;
    cursor: pointer;
}

button:hover {
    background-color: #45a049;
}


.foto-previsualizacion{
    width: 100%;
}
</style>