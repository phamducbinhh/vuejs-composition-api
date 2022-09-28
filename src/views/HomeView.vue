<script>
import {
  reactive,
  computed,
  watch,
  onBeforeMount,
  onMounted,
  onBeforeUnmount,
  onUnmounted,
  onActivated,
  onDeactivated,
  onBeforeUpdate,
  onUpdated,
} from "vue";
//code kiểu vue2 option api
export default {
  data() {
    return {
      //giá trị khởi tạo tương tự như useState React
      count: 0,
      counterTitle: "My counter",
    };
  },
  //phương thức tương tự thực thi 1 hàm để xử lý logic của hàm đó
  methods: {
    inCreaseCounter() {
      this.count++;
    },

    deCreaseCounter() {
      if (this.count > 0) {
        this.count--;
      }
    },
  },
  //computed vue property xây dựng phương thức tính số chẵn lẻ cho biến count
  computed: {
    oddOrEven() {
      if (this.count % 2 === 0) {
        return "chan";
      } else {
        return "le";
      }
    },
  },
  //theo dõi trạng thái thay đổi từ oldCount = > newCount
  watch: {
    count(newCount, oldCount) {
      console.log("newCount", newCount);
      console.log("oldCount", oldCount);
      if (newCount == 20) alert("ok");
    },
  },
  //lifecycle
  mounted() {
    //khi dữ liệu thay đổi đồng thời component render
    console.log("mounted");
  },
  unmounted() {
    //trước khi trạng thái thay đổi thì trạng thái cũ sẽ mounted hoặc khi rời khỏi 1 component
    console.log("unmounted");
  },
};
// code kiểu vue 3 composition api
// export default {
//   setup() {
//     //giá trị khởi tạo tương tự như useState React == sử dụng ref
//     // const count = ref(0);
//     // const counterTitle = ref("My counter");
//     const counterData = reactive({
//       // sử dụng reactive làm giá trị khởi tạo là 1 object gộp chung 2 state  thay cho ref
//       count: 0,
//       title: "My counter",
//     });
//     //computed vue property xây dựng phương thức tính số chẵn lẻ cho biến counterData.count
//     const oddOrEven = computed(() => {
//       if (counterData.count % 2 === 0) {
//         return "chan";
//       } else {
//         return "le";
//       }
//     });
//     //watch theo dõi sự thay đổi của data
//     watch(
//       () => counterData.count,
//       (newCount, oldCount) => {
//         console.log("newCount", newCount);
//         console.log("oldCount", oldCount);
//       }
//     );
//     const inCreaseCounter = () => {
//       counterData.count++;
//     };
//     const deCreaseCounter = () => {
//       if (counterData.count > 0) {
//         counterData.count--;
//       }
//     };
//     //lifecycle hooks
//     onBeforeMount(() => {
//       console.log("onBeforeMount");
//     });
//     onMounted(() => {
//       console.log("onMounted");
//     });
//     onBeforeUnmount(() => {
//       console.log("onBeforeUnmount");
//     });
//     onUnmounted(() => {
//       console.log("onUnmounted");
//     });
//     onActivated(() => {
//       console.log("onActivated");
//     });
//     onDeactivated(() => {
//       console.log("onDeactivated");
//     });
//     onBeforeUpdate(() => {
//       console.log("onBeforeUpdate");
//     });
//     onUpdated(() => {
//       console.log("onUpdated");
//     });
//     return {
//       oddOrEven,
//       inCreaseCounter,
//       deCreaseCounter,
//       counterData,
//     };
//   },
// };
</script>

<template>
  <div class="home">
    <h3>{{ counterTitle }}</h3>
    <div>
      <button class="btn" @click="deCreaseCounter">-</button>
      <span class="counter">{{ count }}</span>
      <button class="btn" @click="inCreaseCounter">+</button>
    </div>

    <p>Thí counter is {{ oddOrEven }}</p>
    <div class="edit">
      <h4>Edit Counter title:</h4>
      <input v-model="counterTitle" type="text" />
    </div>
  </div>
</template>

<style scoped>
.home {
  text-align: center;
  padding: 20px;
}
.btn {
  font-size: 40px;
  margin: 10px;
}
.edit {
  margin-top: 60px;
}
</style>
