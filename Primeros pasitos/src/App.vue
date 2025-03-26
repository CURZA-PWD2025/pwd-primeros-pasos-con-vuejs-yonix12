<script setup>
import MostrarDatos from './components/MostrarDatos.vue'   
import {ref} from 'vue'
const nombreUsuario=ref("")
const email=ref("")
const password=ref("")
const edad=ref(null)
const Usuario=ref(null)

function guardarDatos(){
  if(nombreUsuario.value===""||email.value===""||password.value===""||edad.value===null||edad.value===""){
    alert("Tienes que rellenar los datos")
    return;
  }else{
  Usuario.value= {
  black_nib:nombreUsuario.value,
  "e-mail":email.value,
  lock:password.value,
  baby:edad.value,

  Calcularedad: function(){
 if(!this.baby) return "Fecha no válida"
 let fechaNacimiento=new Date(this.baby)
 let hoy= new Date()
 let edadCalculada = hoy.getFullYear() - fechaNacimiento.getFullYear(); // Diferencia de años
 let mesNacimiento=fechaNacimiento.getMonth();
 let diaNacimiento=fechaNacimiento.getDate();
 let mesActual=hoy.getMonth()
 let diaActual=hoy.getDate();
 if (mesNacimiento > mesActual || (mesNacimiento === mesActual && diaNacimiento > diaActual)) {
  edadCalculada--; 
  }
  return edadCalculada
},
}
console.log("Usuario guardado:", Usuario.value)
console.log(`La edad calculada es: ${Usuario.value.Calcularedad()}`);
alert(`Tu nombre de usuario ingresado es ${nombreUsuario.value}\nTu correo es: ${email.value}\nTu contraseña es: ${password.value} \nTu edad es de ${Usuario.value.Calcularedad()}`)

nombreUsuario.value=""
email.value=""
password.value=""
edad.value=""
  }

}


</script>

<template>
  <h1>Mi primeros pasitos en Vue</h1>
  <form >
    <fieldset>
      <legend>Rellene los campos</legend>
<label for="nombre">Nombre de usuario:</label>
<input type="text" placeholder="Ingrese su nombre" id="nombre" v-model="nombreUsuario">
<label for="email">Ingrese su email:</label>
<input type="email" name="email" id="email" placeholder="Ejemplo@hola.com" v-model="email">
<label for="password">Ingrese su password</label>
<input type="password" name="password" id="password" placeholder="****" v-model="password">
<label for="date">Ingrese su año de nacimiento:</label>
<input type="date" name="date" id="date" v-model="edad">
<input type="button" value="Guardar datos" @click="guardarDatos" id="Guarda">
</fieldset>
</form>

<MostrarDatos :usuario="Usuario" />
</template>

<style scoped>

</style>
