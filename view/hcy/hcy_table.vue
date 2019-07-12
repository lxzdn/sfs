<template>  	
    <div style="margin:0 auto;">
		<Table :columns="columns1" :data="productList"></Table>
		<Page :total="totalPage" :current="currentPage" :page-size="pageSize" :page-size-opts="arrPageSize"
			@on-change="changePage" show-total />

    </div>
</template>
<script>
let productList = [];
for (let i = 0; i < 99; i++) {
    productList.push({
        name: "第" + i + "个",
        age: Math.random() * 200
    });
}
export default {
    data() {
        return {
			 columns1: [
                    {
                        title: 'Name',
                        key: 'name'
                    },
                    {
                        title: 'Age',
                        key: 'age'
                    },
                    
                ],

            productList, 
            totalPage: 10, 
            currentPage: 1, 
            pageSize: 10, 
			arrPageSize: [4],
            currentPageData: [] 
        };
    },
    mounted() {
        this.totalPage = Math.ceil(this.productList.length / this.pageSize);
        this.totalPage = this.totalPage == 0 ? 1 : this.totalPage;
        this.getCurrentPageData();
    },
    methods: {
    		changePage(value) {
    
    				console.log(this.productList.length);
    				this.currentPage = value;
    				var _start = ( value - 1 ) * this.pageSize;
    				var _end = value * this.pageSize;
    				this.productList = this.productList .slice(_start,_end);
    		},
    		propage() {
    				this.loading = true;
    		},
    		remove(index) {
    				this.productList.splice(index, 1);
    		}
    },
};
</script>
