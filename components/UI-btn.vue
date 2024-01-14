<template>
  <button v-if="type == 'header'" class="action-btn" @click="scrollToForm" >
    <slot></slot>
  </button>
  <button v-else class="action-btn form-btn" :style="{ marginBottom: mb }">
    <slot></slot>
  </button>
</template>

<script setup>

const scrollToForm = () => {
  // const formScrollElement = document.getElementById('form-scroll');
  const formScrollElementContact = document.getElementById('form-scroll-Contact');
  // if (formScrollElement) {
  //   formScrollElement.scrollIntoView({ behavior: 'smooth' });
  // } else 
  if (formScrollElementContact) {
    formScrollElementContact.scrollIntoView({ behavior: 'smooth' });
  } else {
    window.location.href="/Contact"
  }
};


const props = defineProps({
  type: {
    type: String,
    required: false,
    default: "header",
  },
  mb: {
    type: String,
    required: false,
  },
});   
</script>

<style lang="scss">
.action-btn {
  cursor: pointer;
  font-size: 16px;
  font-weight: 700;
  line-height: 22px;
  border: none;
  color: #f9fafb;
  background-color: #0ea5e9;
  height: Hug(34px);
  width: Hug(120px);
  display: flex;
  justify-content: center;
  align-items: center;
  border-radius: 5px;
  padding: 6px 10px;
  transition: 0.3s;
  /* margin-bottom: 8px */
}
@media (hover: hover){
  .action-btn:hover {
    background-color: #0484c7;
    transition: 0.5s;
  }
}

@media (hover: none){
  .action-btn:active {
    color: #f9fafb;
    background-color: #0ea5e9;
    transition: 0.3s;
  }
}


.form-btn {
  // font-size: 16px;
  // font-weight: 700;
  // line-height: 22px;
  width: 125px;

  // height: 34px;
  // padding: 6px, 10px, 6px, 10px;
  // border-radius: 4px;
  // gap: 10px;
  // background-color: #0EA5E9;
  // border: none;
  // color: white;
  // cursor: pointer;
  // transition: 0.3s;
  // margin-bottom: 8px;
  @media screen and (max-width: 425px) {
    width: 355px;
    margin-bottom: 10px;
  }
}
</style>
