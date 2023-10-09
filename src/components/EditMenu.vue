<script setup>
import { ref, reactive } from "vue";

const back = ref(false);
const forward = ref(false);

const goBack = () => {
  if (document.execCommand("undo")) {
    back.value = true;
    forward.value = false;
  }
  // window.history.back();
};
const goForward = () => {
  if (document.execCommand("redo")) {
    forward.value = true;
    back.value = false;
  }
  // window.history.forward();
};
const textInTitle = () => {
  const selectedText = window.getSelection().toString();
  if (selectedText) {
    const newHeading = document.createElement("h1");
    newHeading.textContent = selectedText;

    const range = window.getSelection().getRangeAt(0);
    range.deleteContents();
    range.insertNode(newHeading);
  }
};
const titleInText = () => {
  const selectedText = window.getSelection().toString();
  if (selectedText) {
    const newText = document.createElement("p");
    newText.textContent = selectedText;

    const range = window.getSelection().getRangeAt(0);
    range.deleteContents();
    range.insertNode(newText);
  }
};
const insertImage = () => {
  const imageUrl = prompt("Пожалуйста, введите URL изображения");
  if (imageUrl) {
    const image = document.createElement("img");
    console.log(image);
    image.src = imageUrl;

    const range = window.getSelection().getRangeAt(0);
    range.insertNode(image);
  }
};
</script>

<template>
  <div class="wrapper">
    <!-- Меню редактирования -->
    <div class="edit-menu">
      <button @click="goBack" class="btn">
        <img src="../assets/icon/back.svg" alt="img" />
      </button>
      <button @click="goForward" class="btn">
        <img src="../assets/icon/forward.svg" alt="img" />
      </button>
      <button @click="textInTitle" class="btn">
        <img src="../assets/icon/title.svg" alt="img" />
      </button>
      <button @click="titleInText" class="btn">
        <img src="../assets/icon/text.svg" alt="img" />
      </button>
      <button @click="insertImage" class="btn">
        <img src="../assets/icon/image.svg" alt="img" />
      </button>
    </div>

    <!-- Контент страницы -->
    <div class="content">
      <p ref="content" class="editable-text" contenteditable="true">
        Таким образом консультация с широким активом представляет собой
        интересный эксперимент проверки позиций, занимаемых участниками в
        отношении поставленных задач. С другой стороны постоянное
        информационно-пропагандистское обеспечение нашей деятельности
        представляет собой интересный эксперимент проверки форм развития.
        Идейные соображения высшего порядка, а также укрепление и развитие
        структуры влечет за собой процесс внедрения и модернизации
        соответствующий условий активизации. Задача организации, в особенности
        же реализация намеченных плановых заданий играет важную роль в
        формировании дальнейших направлений развития. Повседневная практика
        показывает, что постоянное информационно-пропагандистское обеспечение
        нашей деятельности играет важную роль в формировании существенных
        финансовых и административных условий.
      </p>

      <h1>Смотрите какие обезьянки</h1>
      <img src="../assets/monkeys.png" alt="img" />

      <p ref="content" class="editable-text" contenteditable="true">
        Таким образом консультация с широким активом представляет собой
        интересный эксперимент проверки позиций, занимаемых участниками в
        отношении поставленных задач. С другой стороны постоянное
        информационно-пропагандистское обеспечение нашей деятельности
        представляет собой интересный эксперимент проверки форм развития.
        Идейные соображения высшего порядка, а также укрепление и развитие
        структуры влечет за собой процесс внедрения и модернизации
        соответствующий условий активизации. Задача организации, в особенности
        же реализация намеченных плановых заданий играет важную роль в
        формировании дальнейших направлений развития. Повседневная практика
        показывает, что постоянное информационно-пропагандистское обеспечение
        нашей деятельности играет важную роль в формировании существенных
        финансовых и административных условий.
      </p>
      <p ref="content" class="editable-text" contenteditable="true">
        Товарищи! новая модель организационной деятельности требуют от нас
        анализа направлений прогрессивного развития. Задача организации, в
        особенности же постоянный количественный рост и сфера нашей активности
        требуют от нас анализа позиций, занимаемых участниками в отношении
        поставленных задач. Задача организации, в особенности же реализация
        намеченных плановых заданий требуют от нас анализа системы обучения
        кадров, соответствует насущным потребностям.
      </p>
    </div>
  </div>
</template>

<style scoped>
.wrapper {
  line-height: 23px;
  font-size: 18px;
  color: #eaeaea;
  padding: 50px;
  position: absolute;
}
.edit-menu {
  display: flex;
  flex-direction: row;
  gap: 10px;
  margin-bottom: 40px;
}
.btn {
  width: 40px;
  height: 40px;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  padding: 10px;
  background-color: #282828;
  display: flex;
  align-items: center;
  justify-content: center;
}
.content {
  display: flex;
  flex-direction: column;
  gap: 30px;
}
.editable-text:focus {
  outline: none;
}
</style>
