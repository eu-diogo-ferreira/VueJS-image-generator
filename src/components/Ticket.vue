<template>
  <div class="container">
    <button @click="save">Imprimir</button>
    <div class="ticket"  ref="outputRef">
      <div class="stub">
        <div class="top">
          <span class="admit">Ingresso</span>
          <span class="line"></span>
          <span class="num">
            Código
            <span>31415926</span>
          </span>
        </div>
        <div class="number">1</div>
        <div class="invite">Arik Bartzadok</div>
      </div>
      <div class="check">
        <div class="big">
          GitHub <br />
          Repo.
        </div>
        <div class="number">#1</div>
        <div class="info">
          <section>
            <div class="title">Data</div>
            <div>01/01/2021</div>
          </section>
          <section>
            <div class="title">Promovido por</div>
            <div>GitHub</div>
          </section>
          <section>
            <div class="title">Ingresso número</div>
            <div>31415926</div>
          </section>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
// import { ref } from "vue"
import { toPng } from "dom-to-image-retina"

export default {
  name: "Ticket",
  props: {},
  data: () => {
    return {};
  },
  beforeMount() {},
  methods: {
    save() {
      // const scale = 1
      const outputRef = this.$refs

      if (!outputRef.outputRef) return

      toPng(outputRef.outputRef, {
        
        quality: 1 }).then((dataUrl) => {
        const link = document.createElement("a")
        link.download = "image.png"
        link.href = dataUrl
        link.click()
      }).catch(function (error) {
        console.error('oops, something went wrong!', error)
      })
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.ticket {
  width: 100%;
  height: auto;
  display: flex;
  justify-content: center;
  align-items: center;
  margin: 20px auto;

  transition: 1s;
}
.ticket .stub,
.ticket .check {
  box-sizing: border-box;
}
.ticket:hover {
  transform: scale(1.1);
}
.stub {
  background: rgb(0, 219, 201);
  height: 250px;
  width: 250px;
  color: white;
  padding: 20px;
  position: relative;
}
.stub:before {
  content: "";
  position: absolute;
  top: 0;
  right: 0;
  border-top: 20px solid #fff;
  border-left: 20px solid rgb(0, 219, 201);
  width: 0;
}
.stub:after {
  content: "";
  position: absolute;
  bottom: 0;
  right: 0;
  border-bottom: 20px solid #fff;
  border-left: 20px solid rgb(0, 219, 201);
  width: 0;
}
.stub .top {
  display: flex;
  align-items: center;
  height: 40px;
  text-transform: uppercase;
}
.stub .top .line {
  display: block;
  background: #fff;
  height: 40px;
  width: 3px;
  margin: 0 20px;
}
.stub .top .num {
  font-size: 10px;
}
.stub .top .num span {
  color: #000;
}
.stub .number {
  position: absolute;
  left: 40px;
  font-size: 150px;
  font-weight: bold;
}
.stub .invite {
  position: absolute;
  left: 150px;
  bottom: 45px;
  color: #000;
  width: 20%;
}
.stub .invite:before {
  content: "";
  background: #fff;
  display: block;
  width: 40px;
  height: 3px;
  margin-bottom: 5px;
}
.check {
  background: #fff;
  height: 250px;
  width: 450px;
  padding: 40px;
  position: relative;
  border-top-right-radius: 1.5em;
  border-bottom-right-radius: 1.5em;
}
.check:before {
  content: "";
  position: absolute;
  top: 0;
  left: 0;
  border-top: 20px solid #fff;
  border-right: 20px solid #fff;
  width: 0;
}
.check:after {
  content: "";
  position: absolute;
  bottom: 0;
  left: 0;
  border-bottom: 20px solid #fff;
  border-right: 20px solid #fff;
  width: 0;
}
.check .big {
  font-size: 80px;
  font-weight: 900;
  line-height: 0.8em;
}
.check .number {
  position: absolute;
  top: 50px;
  right: 50px;
  color: rgb(0, 219, 201);
  font-size: 40px;
}
.check .info {
  display: flex;
  justify-content: flex-start;
  font-size: 12px;
  margin-top: 20px;
  width: 100%;
}
.check .info section {
  margin-right: 50px;
}
.check .info section:before {
  content: "";
  background: rgb(0, 219, 201);
  display: block;
  width: 40px;
  height: 3px;
  margin-bottom: 5px;
}
.check .info section .title {
  font-size: 10px;
  text-transform: uppercase;
}
</style>
