<template>
  <div class="group">
    <div
      class="wrapper"
      id="itemKey"
    >
      <h3>使用数组元素里面的唯一标识符作为<code>key</code></h3>
      <p>这个 demo 正常，元素会淡入淡出</p>
      <button
        class="btn"
        @click="itemClick"
      >Add</button>
      <section>
        <transition-group
          tag="ul"
          name="fade"
        >
          <li
            v-for="(item, index) in itemList"
            :key="item"
          >{{item}}<span @click="itemDelete(index)">X</span></li>
        </transition-group>
      </section>
    </div>
    <div
      class="wrapper"
      id="indexKey"
    >
      <h3>使用数组元素里面的<code>index</code>作为<code>key</code></h3>
      <p>这个 demo 存在 bug，只会是最后一个元素淡入淡出</p>
      <button
        class="btn"
        @click="indexClick"
      >Add</button>
      <section>
        <transition-group
          tag="ul"
          name="fade"
        >
          <li
            v-for="(item, index) in indexList"
            :key="index"
          >{{item}}<span @click="indexDelete(index)">X</span>
          </li>
        </transition-group>
      </section>
    </div>
    <div
      class="wrapper"
      id="mixKey"
    >
      <h3>使用数组元素里面的<code>index</code>和变量混合作为<code>key</code></h3>
      <p>这个 demo 也存在 bug，不能够正常工作，每次都会重新刷新点击元素，元素&下面所有元素都会淡入淡出</p>
      <button
        class="btn"
        @click="mixClick"
      >Add</button>
      <section>
        <transition-group
          tag="ul"
          name="fade"
        >
          <li
            v-for="(item, index) in mixList"
            :key="item + index"
          >{{item}}<span @click="mixDelete(index)">X</span></li>
        </transition-group>
      </section>
    </div>
  </div>
</template>

<script>
export default {
    name: "Group",
    data() {
        return {
            itemList: ['transition1', 'transition2', 'transition3', 'transition4', 'transition5', 'transition6'],
            indexList: ['transition1', 'transition2', 'transition3', 'transition4', 'transition5', 'transition6'],
            mixList: ['transition1', 'transition2', 'transition3', 'transition4', 'transition5', 'transition6']
        }
    },
    methods: {
        itemClick() {
            const maxL = this.itemList.map(v => ~~v.slice(10))
            this.itemList.push('transition' + (Math.max(...maxL)+1))
        },
        indexClick() {
            const maxL = this.indexList.map(v => ~~v.slice(10))
            this.indexList.push('transition' + (Math.max(...maxL)+1))
        },
        mixClick() {
            const maxL = this.mixList.map(v => ~~v.slice(10))
            this.mixList.push('transition' + (Math.max(...maxL)+1))
        },
        itemDelete(index) {
            this.itemList.splice(index, 1);
        },
        indexDelete(index) {
            this.indexList.splice(index, 1);
        },
        mixDelete(index) {
            this.mixList.splice(index, 1);
        }
    }
}
</script>

<style scoped>
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s;
}

.fade-enter,
.fade-leave-to {
  opacity: 0;
}

.group {
  font-family: sans;
  display: flex;
  display: -webkit-flex;
  flex-direction: row;
  align-items: flex-start;
  margin: 0 auto;
  margin-top: 30px;
  color: #fff;
  text-align: left;
  min-height: calc(100% - 120px);
  margin-bottom: 10px;
}

.wrapper {
  flex: 1;
  margin: 0 15px;
  padding: 20px;
  background: lightcoral;
}
@media screen and (max-width: 600px) {
  .group {
    flex-direction: column;
    align-items: normal;
  }
  .wrapper {
    margin-top: 10px;
  }
}

h3 {
  font-size: 1rem;
}
p {
  font-size: 0.75rem;
}

.wrapper li {
  box-sizing: border-box;
  position: relative;
  width: 100%;
  padding: 0.5vw 1vh;
  background: #f1a9a0;
  margin-top: 0.5vh;
  border-radius: 3px;
}

.wrapper li span {
  position: absolute;
  right: 2%;
  cursor: pointer;
}

.wrapper li span:hover {
  font-weight: 800;
}

.btn {
  outline: 0;
  border: none;
  padding: 0.2vw 0.5vh;
  border-radius: 5%;
  margin: 2vh 0;
  color: #fff;
  background: #c0392b;
  cursor: pointer;
  opacity: 0.8;
}

.btn:hover {
  font-weight: 600;
  opacity: 1;
}
</style>