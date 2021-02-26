<template>
	<view>
		<view class="">
			<Exchange v-for="item in Object.keys(totalData)" :key="item" :title="item" :categroies="totalData[item]" @changeCover="showCover=!showCover;" />
		</view>
		<MessageBox v-if="showCover" @changeCover="showCover=!showCover;"></MessageBox>
		<Cover v-if="showCover"></Cover>
	</view>
</template>

<script>
	import Exchange from "../../components/Exchange.vue"
	import Cover from "../../components/Cover.vue"
	import MessageBox from "../../components/MessageBox.vue"
	export default {
		components: {
			Exchange,
			Cover,
			MessageBox
		},
		data() {
			return {
				totalData: {
					"上海期货交易所": ["沪铜", "沪铝", "沪锌", "沪铅", "沪镍", "沪锡", "黄金", "白银", "螺纹", "线材", "热卷", "燃油", "沥青", "橡胶", "纸浆", "不锈钢"],
					"大连商品交易所": ["豆一", "豆二", "玉米", "豆粕", "豆油", "棕榈油", "塑料", "PVC", "焦煤", "焦炭", "铁矿石", "鸡蛋", "纤维板", "胶合板", "PP", "玉米淀粉",
						"乙二醇", "粳米", "苯乙烯", "液化石油气", "生猪"
					],
					"郑州商品交易所": ["普麦", "强麦", "白糖", "棉花", "PTA", "菜油", "早籼", "甲醇", "玻璃", "菜籽", "菜粕", "动力煤", "粳稻", "晚籼", "硅铁", "猛硅", "棉纱",
						"苹果", "红枣", "尿素", "纯碱", "短纤", "花生"
					],
					"上海国际能源交易中心": ["国际铜", "低硫燃料油", "20号胶", "原油"],
					"中国金融期货交易所": ["中证500指数", "沪深300指数", "上证50指数", "10年期国债", "5年期国债", "2年期国债"]
				},
				showCover: false
			}
		},
		methods: {},
		onInit() {}
	}
</script>

<style scoped>
</style>
