<template>
  <div class="container">
    <div class="header font">
      <div class="logo">
        <img src="/funabashilogo.png" alt="" />
      </div>
      <div style="width: 100%;">サービス名 [船橋市 戸籍住民課]</div>
    </div>
    <div class="body">
      <div class="side">
        <div class="title">
          窓口一覧
        </div>
        <div class="side-menu isActive">住基異動</div>
        <div class="side-menu">印鑑異動</div>
        <div class="side-menu">カード</div>
        <div class="side-menu">証明</div>
      </div>
      <div class="main">
        <div class="main-toolbar">
          <p>住基異動 進捗</p>
        </div>
        <div class="main-button">
          <button><p>新規受付</p></button>
        </div>
        <div class="main-tabs">
          <div class="tab isActive">入力待ち</div>
          <div class="tab">決裁待ち</div>
          <div class="tab">完了</div>
          <div class="tab">保留中</div>
        </div>
        <div class="main-card-wapper">
          <div class="card titlewapper">
            <div class="card-item-title" style="width: 10%;">受付番号</div>
            <div class="card-item-title" style="width: 10%;">受付時間</div>
            <div class="card-item-title" style="width: 10%;">待ち時間</div>
            <div class="card-item-title" style="width: 20%;">受付内容</div>
            <div class="card-item-title" style="width: 20%;">特記</div>
            <div class="card-item-title" style="width: 10%;"></div>
            <div class="card-item-title non-border" style="width: 10%;"></div>
          </div>
          <div v-for="item in tickets" :key="item" class="card">
            <div class="card-item number" style="width: 10%;">
              {{ item.number }}
            </div>
            <div class="card-item start-time" style="width: 10%;">
              {{ item.startTime }}
            </div>
            <div class="card-item waiting-time" style="width: 10%;">
              {{ item.waitingTime }}
            </div>
            <div class="card-item orders" style="width: 20%;">
              <div v-for="order in item.orders" :key="order" class="tag">
                {{ order }}
              </div>
            </div>
            <div class="card-item tags" style="width: 20%;">
              <div v-for="tag in item.tags" :key="tag" class="tag">
                {{ tag }}
              </div>
            </div>
            <div
              @click="onClick(item)"
              class="card-item button"
              style="width: 10%;"
            >
              {{ item.isPending === true ? '保留中' : '保留' }}
            </div>
            <div class="card-item button" style="width: 10%;">
              開始
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      hoge: 'hoge',
      tickets: [
        {
          number: 15,
          startTime: '10:00',
          waitingTime: '10分',
          orders: ['住基異動', '印鑑異動', 'カード', '証明'],
          tags: ['戸籍異動有'],
          status: '入力待ち',
          isPending: false,
          isFinished: false
        },
        {
          number: 16,
          startTime: '10:05',
          waitingTime: '5分',
          orders: ['住基異動', 'カード', '証明'],
          tags: [],
          status: '入力待ち',
          isPending: false,
          isFinished: false
        },
        {
          number: 17,
          startTime: '10:08',
          waitingTime: '2分',
          orders: ['カード', '証明'],
          tags: [],
          status: '入力待ち',
          isPending: false,
          isFinished: false
        },
        {
          number: 18,
          startTime: '10:09',
          waitingTime: '1分',
          orders: ['住基異動', '印鑑異動', 'カード', '証明'],
          tags: ['複数異動'],
          status: '入力待ち',
          isPending: false,
          isFinished: false
        },
        {
          number: 19,
          startTime: '10:09',
          waitingTime: '1分',
          orders: ['住基異動', '印鑑異動', 'カード', '証明'],
          tags: ['戸籍異動有'],
          status: '入力待ち',
          isPending: false,
          isFinished: false
        }
      ]
    }
  },
  methods: {
    onClick(item) {
      console.log('before', item)
    }
  }
}
</script>

<style>
/* 共通 */
.font {
  font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
}

/* レイアウト */
.container {
  margin: 0 auto;
  height: 100vh;
  display: flex;
  flex-direction: column;
  text-align: center;
}

.header {
  top: 0;
  width: 100%;
  height: 50px;
  padding: 5px;
  border-bottom: thin solid #cdcdcd;
  display: flex;
  justify-content: flex-start;
}
.body {
  width: 100%;
  height: 100%;
  display: flex;
  flex-direction: row;
}
.side {
  width: 20%;
  height: 100%;
  border-right: thin solid #cdcdcd;
}
.main {
  width: 80%;
  height: 100%;
}

/* サイド */
.side > .title {
  margin: 30px;
  padding: 10px;
  background-color: #cdcdcd;
}
.side > .side-menu {
  margin: 20px;
  border-bottom: thin solid #cdcdcd;
  color: #cdcdcd;
}

.side-menu.isActive {
  color: #000;
}
/* ヘッダー */
.logo {
  width: 30px;
  height: 30px;
}
.logo > img {
  width: 100%;
  height: 100%;
}
/* メイン */
.main-toolbar {
  background-color: #fff;
}
.main-button {
  display: flex;
  flex-direction: row-reverse;
  background-color: #cdcdcd;
  padding-top: 5px;
  padding-right: 30px;
}
button {
  width: 100px;
  height: 40px;
  background-color: #fff;
  border-radius: 5px;
}
.main-tabs {
  padding: 0 20px;

  display: flex;
  flex-direction: row;
  background-color: #cdcdcd;
}
.tab {
  width: 100px;
  border: thin solid #cdcdcd;
  border-top-right-radius: 10px;
  /* border-top-left-radius: 5px; */
  padding: 10px;
  margin-right: 3px;
  background-color: #fff;
}
.tab.isActive {
  border-bottom: none;
}
.main-card-wapper {
  padding: 20px;
}
/* カード */
.card {
  display: flex;
  flex-direction: row;
  border: thin solid #cdcdcd;
  padding: 10px;
}
.card-item {
  min-height: 80px;
  flex-grow: 1;
  vertical-align: middle;
  margin: 1px;
}
.titlewapper {
  border: none;
}
.card-item-title {
  flex-grow: 1;
  border-left: thin solid #cdcdcd;
}
.non-border {
  border: none;
}
.button {
  border: thin solid #cdcdcd;
  /* border-radius: 5px; */
}
.orders {
  display: flex;
  flex-wrap: wrap;
}
.tags {
  display: flex;
  flex-wrap: wrap;
}
.tag {
  height: 30px;
  border: thin solid #cdcdcd;
  border-radius: 7px;
  margin: 1px;
}
</style>
