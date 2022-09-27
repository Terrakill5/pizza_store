<template>
	<div>
		<input
    :type="landingProps.tipo"
    required
    :value="landingProps.modelValue"
    v-on:input="updateValue($event.target.value)"
	:placeholder="landingProps.enunciado"
  />
  <label class="lbl-nombre">
    <span class="text-nomb">{{ landingProps.enunciado }}</span>
  </label>
	</div>
  
</template>

<script setup>
import { defineProps, defineEmits } from "vue";
const landingProps = defineProps({
  modelValue: String,
  tipo: String,
  enunciado: String,
  error: Boolean,
});
const emit = defineEmits(["update:modelValue"]);

function updateValue(value) {
  emit("update:modelValue", value);
}
</script>

<style scoped>
input {
  width: 100%;
  height: 100%;
  background: none;
  color: black;
  padding-top: 20px;
  border: none;
  outline: 0px;
}

.lbl-nombre {
  position: absolute;
  bottom: 0;
  left: 0;
  width: 100%;
  height: 100%;
  pointer-events: none;
  border-bottom: 1px solid goldenrod;
}

.lbl-nombre:after {
  content: "";
  position: absolute;
  left: 0;
  bottom: -1px;
  width: 100%;
  height: 100%;
  border-bottom: 3px solid goldenrod;
  transform: translateX(-100%);
  transition: all 0.3s ease;
}

.text-nomb {
  position: absolute;
  bottom: 5px;
  left: 0;
  transition: all 0.3s ease;
  color: transparent;
}

input:focus + .lbl-nombre .text-nomb,
.form input:valid + .lbl-nombre .text-nomb {
  transform: translateY(-150%);
  font-size: 14px;
  color: black;
}
input:focus + .lbl-nombre:after,
.form input:valid + .lbl-nombre:after {
  transform: translateX(0%);
}
</style>
