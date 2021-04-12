<template>
    <div id="app">
        <cart-header></cart-header>
        <div v-show="showAll"><!-- showAll 모델이 true면 보여줘라 -->
            <h2>전체 목록</h2>
            <!-- v-for : Collection 모델을 루프 -->
            <ul>
                <!-- 가급적 Key값은 해당 데이터의 유일 식별자로 설정 -->
                <li v-for="(item, index) in items" v-bind:key="index">{{ item.name }}</li>
            </ul>
        </div>
        <!-- 살 물건들 -->
        <shop-list v-bind:shopping-items="items"></shop-list>
        <!-- 입력 창 -->
        <cart-input v-on:add-item="addItem"></cart-input>
        <input type="checkbox" v-model="showOption">산 물건 보기
        <!-- 산 물건들-->
        <bought-list v-on:remove-item="removeItem" v-bind:bought-items="items" v-show="showOption"></bought-list>
        <cart-footer></cart-footer>
    </div>
</template>

<script>
//  컴포넌트 불러오기
import CartHeader from './components/CartHeader.vue';
import CartFooter from './components/CartFooter.vue';
import ShopList from './components/ShopList.vue';
import CartInput from './components/CartInput.vue';
import BougthList from './components/BoughtList.vue';

export default {
  components: { CartHeader },
    //  내부에서 사용할 지역 컴포넌트
    components: {
        "cart-header": CartHeader,
        "cart-footer": CartFooter,
        "shop-list": ShopList,
        "cart-input": CartInput,
        "bought-list": BougthList
    },
    data: function() {
        return {
            items: [
                { name: "무", buy: false },
                { name: "배추", buy: false },
                { name: "쪽파", buy: true },
                { name: "고춧가루", buy: false}
            ],
            showAll: true,  //  전체 목록 보이기 여부
            showOption: true    //  산 목록 보이기 여부
        }
    }
}
</script>