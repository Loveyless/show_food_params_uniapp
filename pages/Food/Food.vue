<template>
	<view class="container">
		<!-- 顶部搜索 -->
		<view class="search">
			<input type="text" v-model="searchText" @confirm="searchFood()" confirm-type="search"
				placeholder="请输入食物名称查询" />
			<image @click="searchFood()" src="../../static/search.png" mode="aspectFill"></image>
		</view>



		<!-- 展示区域 -->
		<view class="main">

			<!-- 每个展示项 -->
			<view class="item" v-for="(item,i) in foodList" :key="i">

				<!-- 顶部title和type -->
				<view class="top">
					<span class="title">{{item.name}}</span>
					<span class="type">{{item.type}}</span>
				</view>

				<!-- 图表 https://ext.dcloud.net.cn/plugin?id=271 -->
				<view class="charts-box">
					<qiun-data-charts type="pie" :chartData="item.chartData" background="none" />
				</view>

				<view v-show="item.isOpen" class="bottom">
					<view class="bottom_item">
						热量:{{item.rl}}
					</view>
					<view class="bottom_item">
						钙(毫克):{{item.gai}}
					</view>
					<view class="bottom_item">
						维生素C:{{item.wsfc}}
					</view>
					<view class="bottom_item">
						铁:{{item.tei}}
					</view>
					<view class="bottom_item">
						镁:{{item.mei}}
					</view>
					<view class="bottom_item">
						膳食纤维:{{item.ssxw}}
					</view>
					<view class="bottom_item">
						锌:{{item.xin}}
					</view>
					<view class="bottom_item">
						维生素A:{{item.wssa}}
					</view>
					<view class="bottom_item">
						胆固醇:{{item.dgc}}
					</view>
					<view class="bottom_item">
						胡萝卜素:{{item.lb}}
					</view>
					<view class="bottom_item">
						视黄醇当量:{{item.shc}}
					</view>
					<view class="bottom_item">
						钾:{{item.jia}}
					</view>
					<view class="bottom_item">
						磷:{{item.ling}}
					</view>
					<view class="bottom_item">
						硒:{{item.xi}}
					</view>
				</view>


				<button @click="changeOpen(i)" type="default">{{!item.isOpen ? "展示更多" : "收起"}}</button>


			</view>

		</view>



	</view>
</template>

<script>
	export default {
		data() {
			return {
				// 要查询的食物
				searchText: "",
				// 查出的食物数组
				foodList: [{
						"name": "稻米(均值)",
						"rl": 346,
						"las": 0.11,
						"gai": 13,
						"dbz": 7.4,
						"su": 0.05,
						"mei": 34,
						"zf": 0.8,
						"ys": 1.9,
						"tei": 2.3,
						"shhf": 77.2,
						"wsfc": 0,
						"meng": 1.29,
						"ssxw": 0.7,
						"wsse": 0.46,
						"xin": 1.7,
						"wssa": 0,
						"dgc": 0,
						"tong": 0.3,
						"lb": 0.6,
						"jia": 103,
						"ling": 110,
						"shc": 13.3,
						"la": 3.8,
						"xi": 2.23,
						"type": "谷类",
						"isOpen": false,
						"chartData": {
							"series": [{
								"data": [{
										"name": "蛋白质",
										"value": 7.4
									},
									{
										"name": "碳水",
										"value": 77.2
									},
									{
										"name": "脂肪",
										"value": 0.8
									}
								]
							}]
						}
					},
					{
						"name": "粳米(标一)",
						"rl": 343,
						"las": 0.16,
						"gai": 11,
						"dbz": 7.7,
						"su": 0.08,
						"mei": 34,
						"zf": 0.6,
						"ys": 1.3,
						"tei": 1.1,
						"shhf": 76.8,
						"wsfc": 0,
						"meng": 1.36,
						"ssxw": 0.6,
						"wsse": 1.01,
						"xin": 1.45,
						"wssa": 0,
						"dgc": 0,
						"tong": 0.19,
						"lb": 0.6,
						"jia": 97,
						"ling": 121,
						"shc": 13.7,
						"la": 2.4,
						"xi": 2.5,
						"type": "谷类",
						"isOpen": false,
						"chartData": {
							"series": [{
								"data": [{
										"name": "蛋白质",
										"value": 7.7
									},
									{
										"name": "碳水",
										"value": 76.8
									},
									{
										"name": "脂肪",
										"value": 0.6
									}
								]
							}]
						}
					},
					{
						"name": "粳米(标二)",
						"rl": 347,
						"las": 0.22,
						"gai": 3,
						"dbz": 8,
						"su": 0.05,
						"mei": 20,
						"zf": 0.6,
						"ys": 2.6,
						"tei": 0.4,
						"shhf": 77.3,
						"wsfc": 0,
						"meng": 0.77,
						"ssxw": 0.4,
						"wsse": 0.53,
						"xin": 0.89,
						"wssa": 0,
						"dgc": 0,
						"tong": 0.28,
						"lb": 0.5,
						"jia": 78,
						"ling": 99,
						"shc": 13.2,
						"la": 0.9,
						"xi": 6.4,
						"type": "谷类",
						"isOpen": false,
						"chartData": {
							"series": [{
								"data": [{
										"name": "蛋白质",
										"value": 8
									},
									{
										"name": "碳水",
										"value": 77.3
									},
									{
										"name": "脂肪",
										"value": 0.6
									}
								]
							}]
						}
					},
					{
						"name": "粳米(标三)",
						"rl": 345,
						"las": 0.33,
						"gai": 5,
						"dbz": 7.2,
						"su": 0.03,
						"mei": 0,
						"zf": 0.8,
						"ys": 3.6,
						"tei": 0.7,
						"shhf": 77.2,
						"wsfc": 0,
						"meng": 0.89,
						"ssxw": 0.4,
						"wsse": 0.3,
						"xin": 0.93,
						"wssa": 0,
						"dgc": 0,
						"tong": 0.28,
						"lb": 0.5,
						"jia": 78,
						"ling": 108,
						"shc": 13.9,
						"la": 1.3,
						"xi": 5.4,
						"type": "谷类",
						"isOpen": false,
						"chartData": {
							"series": [{
								"data": [{
										"name": "蛋白质",
										"value": 7.2
									},
									{
										"name": "碳水",
										"value": 77.2
									},
									{
										"name": "脂肪",
										"value": 0.8
									}
								]
							}]
						}
					},
					{
						"name": "粳米(标四)",
						"rl": 346,
						"las": 0.14,
						"gai": 4,
						"dbz": 7.5,
						"su": 0.05,
						"mei": 20,
						"zf": 0.7,
						"ys": 5.2,
						"tei": 0.7,
						"shhf": 77.4,
						"wsfc": 0,
						"meng": 1.07,
						"ssxw": 0.7,
						"wsse": 0.39,
						"xin": 0.97,
						"wssa": 0,
						"dgc": 0,
						"tong": 0.26,
						"lb": 0.6,
						"jia": 106,
						"ling": 123,
						"shc": 13.1,
						"la": 1.6,
						"xi": 4.87,
						"type": "谷类",
						"isOpen": false,
						"chartData": {
							"series": [{
								"data": [{
										"name": "蛋白质",
										"value": 7.5
									},
									{
										"name": "碳水",
										"value": 77.4
									},
									{
										"name": "脂肪",
										"value": 0.7
									}
								]
							}]
						}
					},
					{
						"name": "粳米(特等)",
						"rl": 334,
						"las": 0.08,
						"gai": 24,
						"dbz": 7.3,
						"su": 0.04,
						"mei": 25,
						"zf": 0.4,
						"ys": 1.1,
						"tei": 0.9,
						"shhf": 75.3,
						"wsfc": 0,
						"meng": 1,
						"ssxw": 0.4,
						"wsse": 0.76,
						"xin": 1.07,
						"wssa": 0,
						"dgc": 0,
						"tong": 0.26,
						"lb": 0.4,
						"jia": 58,
						"ling": 80,
						"shc": 16.2,
						"la": 6.2,
						"xi": 2.49,
						"type": "谷类",
						"isOpen": false,
						"chartData": {
							"series": [{
								"data": [{
										"name": "蛋白质",
										"value": 7.3
									},
									{
										"name": "碳水",
										"value": 75.3
									},
									{
										"name": "脂肪",
										"value": 0.4
									}
								]
							}]
						}
					},
					{
						"name": "籼米(标一)",
						"rl": 346,
						"las": 0.15,
						"gai": 7,
						"dbz": 7.7,
						"su": 0.06,
						"mei": 33,
						"zf": 0.7,
						"ys": 2.1,
						"tei": 1.3,
						"shhf": 77.3,
						"wsfc": 0,
						"meng": 1,
						"ssxw": 0.6,
						"wsse": 0.43,
						"xin": 1.46,
						"wssa": 0,
						"dgc": 0,
						"tong": 0.23,
						"lb": 0.7,
						"jia": 89,
						"ling": 146,
						"shc": 13,
						"la": 2.7,
						"xi": 3.8,
						"type": "谷类",
						"isOpen": false,
						"chartData": {
							"series": [{
								"data": [{
										"name": "蛋白质",
										"value": 7.7
									},
									{
										"name": "碳水",
										"value": 77.3
									},
									{
										"name": "脂肪",
										"value": 0.7
									}
								]
							}]
						}
					},
					{
						"name": "籼米(标准)[机米]",
						"rl": 347,
						"las": 0.09,
						"gai": 12,
						"dbz": 7.9,
						"su": 0.04,
						"mei": 28,
						"zf": 0.6,
						"ys": 1.4,
						"tei": 1.6,
						"shhf": 77.5,
						"wsfc": 0,
						"meng": 1.27,
						"ssxw": 0.8,
						"wsse": 0.54,
						"xin": 1.47,
						"wssa": 0,
						"dgc": 0,
						"tong": 0.29,
						"lb": 0.6,
						"jia": 109,
						"ling": 112,
						"shc": 12.6,
						"la": 1.7,
						"xi": 1.99,
						"type": "谷类",
						"isOpen": false,
						"chartData": {
							"series": [{
								"data": [{
										"name": "蛋白质",
										"value": 7.9
									},
									{
										"name": "碳水",
										"value": 77.5
									},
									{
										"name": "脂肪",
										"value": 0.6
									}
								]
							}]
						}
					},
					{
						"name": "籼米(优标)",
						"rl": 349,
						"las": 0.13,
						"gai": 8,
						"dbz": 8.3,
						"su": 0.02,
						"mei": 13,
						"zf": 1,
						"ys": 2.6,
						"tei": 0.5,
						"shhf": 76.8,
						"wsfc": 0,
						"meng": 1.02,
						"ssxw": 0.5,
						"wsse": 0,
						"xin": 1.6,
						"wssa": 0,
						"dgc": 0,
						"tong": 0.3,
						"lb": 0.6,
						"jia": 64,
						"ling": 85,
						"shc": 12.8,
						"la": 1.2,
						"xi": 6.9,
						"type": "谷类",
						"isOpen": false,
						"chartData": {
							"series": [{
								"data": [{
										"name": "蛋白质",
										"value": 8.3
									},
									{
										"name": "碳水",
										"value": 76.8
									},
									{
										"name": "脂肪",
										"value": 1
									}
								]
							}]
						}
					},
					{
						"name": "黑米",
						"rl": 333,
						"las": 0.33,
						"gai": 12,
						"dbz": 9.4,
						"su": 0.13,
						"mei": 147,
						"zf": 2.5,
						"ys": 7.9,
						"tei": 1.6,
						"shhf": 68.3,
						"wsfc": 0,
						"meng": 1.72,
						"ssxw": 3.9,
						"wsse": 0.22,
						"xin": 3.8,
						"wssa": 0,
						"dgc": 0,
						"tong": 0.15,
						"lb": 1.6,
						"jia": 256,
						"ling": 356,
						"shc": 14.3,
						"la": 7.1,
						"xi": 3.2,
						"type": "谷类",
						"isOpen": false,
						"chartData": {
							"series": [{
								"data": [{
										"name": "蛋白质",
										"value": 9.4
									},
									{
										"name": "碳水",
										"value": 68.3
									},
									{
										"name": "脂肪",
										"value": 2.5
									}
								]
							}]
						}
					},
					{
						"name": "香大米",
						"rl": 346,
						"las": 0,
						"gai": 8,
						"dbz": 12.7,
						"su": 0.08,
						"mei": 12,
						"zf": 0.9,
						"ys": 2.6,
						"tei": 5.1,
						"shhf": 71.8,
						"wsfc": 0,
						"meng": 1.75,
						"ssxw": 0.6,
						"wsse": 0.7,
						"xin": 0.69,
						"wssa": 0,
						"dgc": 0,
						"tong": 0.52,
						"lb": 1.1,
						"jia": 49,
						"ling": 106,
						"shc": 12.9,
						"la": 21.5,
						"xi": 4.6,
						"type": "谷类",
						"isOpen": false,
						"chartData": {
							"series": [{
								"data": [{
										"name": "蛋白质",
										"value": 12.7
									},
									{
										"name": "碳水",
										"value": 71.8
									},
									{
										"name": "脂肪",
										"value": 0.9
									}
								]
							}]
						}
					},
					{
						"name": "糯米[江米](均值)",
						"rl": 348,
						"las": 0.11,
						"gai": 26,
						"dbz": 7.3,
						"su": 0.04,
						"mei": 49,
						"zf": 1,
						"ys": 2.3,
						"tei": 1.4,
						"shhf": 77.5,
						"wsfc": 0,
						"meng": 1.54,
						"ssxw": 0.8,
						"wsse": 1.29,
						"xin": 1.54,
						"wssa": 0,
						"dgc": 0,
						"tong": 0.25,
						"lb": 0.8,
						"jia": 137,
						"ling": 113,
						"shc": 12.6,
						"la": 1.5,
						"xi": 2.71,
						"type": "谷类",
						"isOpen": false,
						"chartData": {
							"series": [{
								"data": [{
										"name": "蛋白质",
										"value": 7.3
									},
									{
										"name": "碳水",
										"value": 77.5
									},
									{
										"name": "脂肪",
										"value": 1
									}
								]
							}]
						}
					},
					{
						"name": "优糯米",
						"rl": 344,
						"las": 0.1,
						"gai": 8,
						"dbz": 9,
						"su": 0.03,
						"mei": 50,
						"zf": 1,
						"ys": 1.9,
						"tei": 0.8,
						"shhf": 74.7,
						"wsfc": 0,
						"meng": 0.86,
						"ssxw": 0.6,
						"wsse": 0.93,
						"xin": 1.2,
						"wssa": 0,
						"dgc": 0,
						"tong": 0.25,
						"lb": 0.5,
						"jia": 136,
						"ling": 48,
						"shc": 14.2,
						"la": 1.2,
						"xi": 2.8,
						"type": "谷类",
						"isOpen": false,
						"chartData": {
							"series": [{
								"data": [{
										"name": "蛋白质",
										"value": 9
									},
									{
										"name": "碳水",
										"value": 74.7
									},
									{
										"name": "脂肪",
										"value": 1
									}
								]
							}]
						}
					},
					{
						"name": "紫红糯米[血糯米]",
						"rl": 343,
						"las": 0.31,
						"gai": 13,
						"dbz": 8.3,
						"su": 0.12,
						"mei": 16,
						"zf": 1.7,
						"ys": 4.2,
						"tei": 3.9,
						"shhf": 73.7,
						"wsfc": 0,
						"meng": 2.37,
						"ssxw": 1.4,
						"wsse": 1.36,
						"xin": 2.16,
						"wssa": 0,
						"dgc": 0,
						"tong": 0.29,
						"lb": 1.1,
						"jia": 219,
						"ling": 183,
						"shc": 13.8,
						"la": 4,
						"xi": 2.88,
						"type": "谷类",
						"isOpen": false,
						"chartData": {
							"series": [{
								"data": [{
										"name": "蛋白质",
										"value": 8.3
									},
									{
										"name": "碳水",
										"value": 73.7
									},
									{
										"name": "脂肪",
										"value": 1.7
									}
								]
							}]
						}
					},
					{
						"name": "粳糯米",
						"rl": 343,
						"las": 0.2,
						"gai": 21,
						"dbz": 7.9,
						"su": 0.05,
						"mei": 42,
						"zf": 0.8,
						"ys": 1.7,
						"tei": 1.9,
						"shhf": 76,
						"wsfc": 0,
						"meng": 1.56,
						"ssxw": 0.7,
						"wsse": 0.08,
						"xin": 1.77,
						"wssa": 0,
						"dgc": 0,
						"tong": 0.24,
						"lb": 0.8,
						"jia": 125,
						"ling": 94,
						"shc": 13.8,
						"la": 2.8,
						"xi": 3.3,
						"type": "谷类",
						"isOpen": false,
						"chartData": {
							"series": [{
								"data": [{
										"name": "蛋白质",
										"value": 7.9
									},
									{
										"name": "碳水",
										"value": 76
									},
									{
										"name": "脂肪",
										"value": 0.8
									}
								]
							}]
						}
					},
					{
						"name": "籼糯米",
						"rl": 352,
						"las": 0.19,
						"gai": 14,
						"dbz": 7.9,
						"su": 0.04,
						"mei": 52,
						"zf": 1.1,
						"ys": 2.3,
						"tei": 1.8,
						"shhf": 77.5,
						"wsfc": 0,
						"meng": 1.31,
						"ssxw": 0.5,
						"wsse": 0,
						"xin": 1.52,
						"wssa": 0,
						"dgc": 0,
						"tong": 0.17,
						"lb": 0.7,
						"jia": 132,
						"ling": 82,
						"shc": 12.3,
						"la": 1.9,
						"xi": 2.4,
						"type": "谷类",
						"isOpen": false,
						"chartData": {
							"series": [{
								"data": [{
										"name": "蛋白质",
										"value": 7.9
									},
									{
										"name": "碳水",
										"value": 77.5
									},
									{
										"name": "脂肪",
										"value": 1.1
									}
								]
							}]
						}
					},
					{
						"name": "米饭(蒸)(均值)",
						"rl": 116,
						"las": 0.02,
						"gai": 7,
						"dbz": 2.6,
						"su": 0.03,
						"mei": 15,
						"zf": 0.3,
						"ys": 1.9,
						"tei": 1.3,
						"shhf": 25.6,
						"wsfc": 0,
						"meng": 0.58,
						"ssxw": 0.3,
						"wsse": 0,
						"xin": 0.92,
						"wssa": 0,
						"dgc": 0,
						"tong": 0.06,
						"lb": 0.3,
						"jia": 30,
						"ling": 62,
						"shc": 70.9,
						"la": 2.5,
						"xi": 0.4,
						"type": "谷类",
						"isOpen": false,
						"chartData": {
							"series": [{
								"data": [{
										"name": "蛋白质",
										"value": 2.6
									},
									{
										"name": "碳水",
										"value": 25.6
									},
									{
										"name": "脂肪",
										"value": 0.3
									}
								]
							}]
						}
					},
					{
						"name": "粳米饭(蒸)",
						"rl": 117,
						"las": 0,
						"gai": 7,
						"dbz": 2.6,
						"su": 0.03,
						"mei": 20,
						"zf": 0.3,
						"ys": 2,
						"tei": 2.2,
						"shhf": 26,
						"wsfc": 0,
						"meng": 0.85,
						"ssxw": 0.2,
						"wsse": 0,
						"xin": 1.36,
						"wssa": 0,
						"dgc": 0,
						"tong": 0.08,
						"lb": 0.3,
						"jia": 39,
						"ling": 62,
						"shc": 70.6,
						"la": 3.3,
						"xi": 0.4,
						"type": "谷类",
						"isOpen": false,
						"chartData": {
							"series": [{
								"data": [{
										"name": "蛋白质",
										"value": 2.6
									},
									{
										"name": "碳水",
										"value": 26
									},
									{
										"name": "脂肪",
										"value": 0.3
									}
								]
							}]
						}
					},
					{
						"name": "籼米饭(蒸)",
						"rl": 114,
						"las": 0.02,
						"gai": 6,
						"dbz": 2.5,
						"su": 0.03,
						"mei": 10,
						"zf": 0.2,
						"ys": 1.7,
						"tei": 0.3,
						"shhf": 25.6,
						"wsfc": 0,
						"meng": 0.31,
						"ssxw": 0.4,
						"wsse": 0,
						"xin": 0.47,
						"wssa": 0,
						"dgc": 0,
						"tong": 0.04,
						"lb": 0.2,
						"jia": 21,
						"ling": 0,
						"shc": 71.1,
						"la": 1.7,
						"xi": 0,
						"type": "谷类",
						"isOpen": false,
						"chartData": {
							"series": [{
								"data": [{
										"name": "蛋白质",
										"value": 2.5
									},
									{
										"name": "碳水",
										"value": 25.6
									},
									{
										"name": "脂肪",
										"value": 0.2
									}
								]
							}]
						}
					},
					{
						"name": "粳米粥",
						"rl": 46,
						"las": 0,
						"gai": 7,
						"dbz": 1.1,
						"su": 0.03,
						"mei": 7,
						"zf": 0.3,
						"ys": 0.2,
						"tei": 0.1,
						"shhf": 9.8,
						"wsfc": 0,
						"meng": 0.2,
						"ssxw": 0.1,
						"wsse": 0,
						"xin": 0.2,
						"wssa": 0,
						"dgc": 0,
						"tong": 0.03,
						"lb": 0.1,
						"jia": 13,
						"ling": 20,
						"shc": 88.6,
						"la": 2.8,
						"xi": 0.2,
						"type": "谷类",
						"isOpen": false,
						"chartData": {
							"series": [{
								"data": [{
										"name": "蛋白质",
										"value": 1.1
									},
									{
										"name": "碳水",
										"value": 9.8
									},
									{
										"name": "脂肪",
										"value": 0.3
									}
								]
							}]
						}
					}
				],
				
				requestURL: "http://api.tianapi.com/nutrient/index?",
				apiKEY: "bba54c417b3678e22505a1ef69b47fd0"
			}
		},
		methods: {
			// 请求数据
			searchFood() {
				uni.showLoading()
				uni.request({
					method: "GET",
					url: `${this.requestURL}key=${this.apiKEY}&word=${this.searchText}&mode=0&num=20`,
					success: (res) => {
						//是否搜索到了内容
						if (res.data.newslist == undefined) {
							uni.showToast({
								title: "没有搜索到内容",
								icon: "error"
							})
						} else {
							//赋值(带了图标属性)
							this.foodList = res.data.newslist.map((v, i, arr) => {
								v.isOpen = false
								v.chartData = {}
								v.chartData.series = [{
									data: [{
											name: "蛋白质",
											value: v.dbz
										},
										{
											name: "碳水",
											value: v.shhf
										},
										{
											name: "脂肪",
											value: v.zf
										},
									]
								}]
								return v
							})
						}
						uni.hideLoading()
					},
					fail: (err) => {
						uni.hideLoading()
					}
				})
			},
			changeOpen(i) {
				console.log(i)
				this.foodList[i].isOpen = !this.foodList[i].isOpen
			}
		}
	}
</script>

<style scoped lang="less">
	.container {
		display: flex;
		flex-direction: column;
		align-items: center;

		.search {
			display: flex;

			input {
				margin-top: 10rpx;
				height: 50rpx;
				padding-left: 15rpx;
				border-radius: 10px 0 0 10px;
				box-sizing: border-box;
				width: 660rpx;
				border: 5rpx solid #d4d4d4;
				border-right: none;
				font-size: 26rpx;
			}

			image {
				margin-top: 10rpx;
				margin-left: -2rpx;
				padding-right: 7rpx;
				height: 50rpx;
				border-radius: 0 10px 10px 0;
				box-sizing: border-box;
				width: 50rpx;
				border: 5rpx solid #d4d4d4;
				border-left: none;
			}
		}

		.main {
			display: flex;
			flex-direction: column;
			align-items: center;
			overflow: auto;

			.item {
				color: #242424;
				width: 700rpx;
				margin-top: 20rpx;
				border: 2px solid #e6e6e6;
				border-radius: 5px;
				display: flex;
				flex-direction: column;
				align-items: center;

				// background-color: yellow;
				.top {
					padding: 16rpx;

					.title {
						font-size: 25rpx;
						margin-right: 15rpx;
					}

					.type {
						font-size: 16rpx;
						color: #595959;
					}
				}

				/* 请根据需求修改图表容器尺寸，如果父容器没有高度图表则会显示异常 */
				.charts-box {
					width: 100%;
					height: 220px;
				}


				.bottom {
					width: 100%;
					display: flex;
					flex-wrap: wrap;
					justify-content: center;

					.bottom_item {
						margin: 7rpx;
						height: 40rpx;
						color: #787878;
						text-align: center;
						font-size: 15rpx;
					}
				}

				button {
					border: none;
					margin-top: 10rpx;
					font-size: 18rpx;
					background-color: #fdfdfd;
					width: 100%;
					height: 60rpx;
					vertical-align: middle;
				}

			}
		}
	}
</style>
