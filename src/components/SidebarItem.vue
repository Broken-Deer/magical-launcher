<template>
  <li class="sidebar-item" @mousedown="onMousedown($event)">
    <i class="fa-regular nav-icon" :id="icon"></i>
    <div class="tooltip" v-if="title">{{ title }}</div>
  </li>
</template>

<script setup lang="ts">
import $ from 'jquery'
defineProps<{
  title?: string,
  icon: string,
  // click?: string,
}>()

function onMousedown(event: MouseEvent) {
  let htmlElement = event.target as HTMLLIElement
  $(htmlElement.lastElementChild).addClass('tooltip-hidden')
  console.log(htmlElement.lastElementChild)
  setTimeout(() => {
    $(htmlElement.lastElementChild).removeClass('tooltip-hidden')
  }, 500);
}
</script>

<style lang="less">
.sidebar-item {
  margin-bottom: 2px;
}

.sidebar-item i {
  pointer-events: none;
}

div.main-sidebar>div {
  margin: 16px 8px 7px 8px;
  height: calc(100% - 26px);
  display: flex;
  flex-direction: column;
}

div.main-sidebar ul.sidebar-links {
  display: flex;
  justify-content: space-between;
  flex-grow: 1;
  flex-direction: column;
}

div.main-sidebar ul.sidebar-links>div {
  width: 100%;
}

div.main-sidebar li:active {
  transform: scale(0.94);
}

div.main-sidebar li {
  transition: transform 0.17s ease;
  width: 100%;
  height: 36px;
  align-items: center;
  border-radius: 6px;
  white-space: nowrap;
  display: flex;
  padding-left: 7.5px;
  position: relative;
}

div.main-sidebar li:hover {
  background-color: #ffffff52;
}

div.main-sidebar .sidebar-links i {
  font-size: calc(17.6px - var(--font-size-error));
  font-weight: 400;
  font-family: "fa-pro";
  font-style: normal;
  width: 24px;
  display: inline-block;
  margin-right: 0.7rem;
  text-align: center;
  flex-shrink: 0;
  padding-left: 3px;
}

div.main-sidebar span {
  display: inline-block;
  white-space: nowrap;
  font-size: calc(14px - var(--font-size-error));
  transition: all 0.2s ease;
}

.sidebar-button {
  width: 40px;
  height: 36px;
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: var(--border-radius-small);
  margin-left: 1.6px;
}

.sidebar-button i {
  font-size: calc(16px - var(--font-size-error));
  font-family: "fa-pro";
  font-style: normal;
  height: 1em;
  width: 1em;
  text-align: center;
  transition: all 0.2s cubic-bezier(0, 0.61, 0.16, 0.98);
}

.sidebar-button:active i {
  transform: scale(0.7, 1);
}

.sidebar-close {
  width: 60px !important;
  margin-right: -60px !important;
}

.sidebar-close span {
  opacity: 0;
}

.tooltip {
  display: flex;
  padding: 6px 8px;
  background: #fff;
  border-radius: var(--border-radius-small);
  position: fixed;
  color: #000;
  margin-left: 38px;
  box-shadow: 0 0 10px #cacaca;
  font-size: calc(13px - var(--font-size-error));
  opacity: 0;
  z-index: 1145141;
  transform: scale(0.9);
  transition: all 200ms ease;
  pointer-events: none;
}

.sidebar-item:hover .tooltip {

  opacity: 1;
  transform: scale(1);
}

.tooltip-hidden {
  opacity: 0 !important;
  transform: scale(1) !important;
}

// .sidebar-item:active .tooltip {
// opacity: 0;
// transform: scale(1);
// }
</style>