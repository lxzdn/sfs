<template>
    <div style="margin:0 auto;">
        <Table :loading="loading" border :columns="columns7" :data="lastdata"></Table>
        <br>
        <div align="center">
        <template>
            <Page :total="total" :current="current" :page-size="pageNum" :page-size-opts="arrPageSize"
              @on-change="changePage" show-total />
        </template>
        </div>
    </div>
</template>
<script>
    export default {
        data() {
            return {
                loading: false,
                current: 1,
                total: 9,
                pageNum: 5,
                arrPageSize: [4],
                lastdata: [
                    {
                        id: 1,
                        name: '肯德基',
                        price: 18,
                        number: '23'
                    }, {
                        id: 2,
                        name: '麦当劳',
                        price: 23,
                        number: 6
                    },
                    {
                        id: 3,
                        name: '必胜客',
                        price: 41,
                        number: 9
                    },
                    {
                        id: 4,
                        name: '德克士',
                        price: 36,
                        number: 13
                    },
                    {
                        id: 5,
                        name: '好利来',
                        price: 46,
                        number: 45
                    },
                    {
                        id: 6,
                        name: '小龙虾',
                        price: 78,
                        number: 56
                    },
                    {
                        id: 7,
                        name: '烤翅',
                        price: 14,
                        number: 45
                    },
                    {
                        id: 8,
                        name: '雪糕',
                        price: 4,
                        number: 104
                    },
					{
						id: 9,
						name: '可乐',
						price: 3,
						number: 220
					},
					{
						id: 10,
						name: '方便面',
						price: 5,
						number: 80
					}
                ],
                columns7: [
                    {
                        title: '编号',
                        key: 'id',
                        width: 100,
                        fixed: 'left',
                        
                    },
                    {
                        title: '商品名称',
                        key: 'name'
                    },
                    {
                        title: '产品最低售价',
                        key: 'price'
                    },
                    {
                        title: '库存',
                        key: 'number'
                    },
                    
                ],
                data6: [
                    {
                    	id: 1,
                    	name: '肯德基',
                    	price: 18,
                    	number: '23'
                    }, {
                    	id: 2,
                    	name: '麦当劳',
                    	price: 23,
                    	number: 6
                    },
                    {
                    	id: 3,
                    	name: '必胜客',
                    	price: 41,
                    	number: 9
                    },
                    {
                    	id: 4,
                    	name: '德克士',
                    	price: 36,
                    	number: 13
                    },
                    {
                    	id: 5,
                    	name: '好利来',
                    	price: 46,
                    	number: 45
                    },
                    {
                    	id: 6,
                    	name: '小龙虾',
                    	price: 78,
                    	number: 56
                    },
                    {
                    	id: 7,
                    	name: '烤翅',
                    	price: 14,
                    	number: 45
                    },
                    {
                    	id: 8,
                    	name: '雪糕',
                    	price: 4,
                    	number: 104
                    },
					{
						id: 9,
						name: '可乐',
						price: 3,
						number: 220
					},
					{
						id: 10,
						name: '方便面',
						price: 5,
						number: 80
					},
                ]
            }
        },
        methods: {
            changePage(value) {
				
                console.log(this.data6.length);
                 this.current = value;
                var _start = ( value - 1 ) * this.pageNum;
                var _end = value * this.pageNum;
                this.lastdata = this.data6 .slice(_start,_end);
            },
            propage() {
                this.loading = true;
            },
            remove(index) {
                this.data6.splice(index, 1);
            }
        },
		  created:function(){
               this.lastdata = this.data6 .slice(0,5);
            },
    }
</script>
<style>
    .pro-page{
        position: fixed;
        height: 500px;
    }
</style>