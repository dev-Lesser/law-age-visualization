<template>
<v-card>
    <v-card-title>
      <v-text-field
        v-model="search"
        append-icon="mdi-magnify"
        label="내용을 검색하세요"
        single-line
        hide-details
        filled
      ></v-text-field>
    </v-card-title>
    <v-data-table
        dense
        :headers="headers"
        :items="this.lawData"
        :search="search"
        class="data-table pa-4"
        height="700"
        fixed-header
        :footer-props="{
            'items-per-page-text': '페이지 단위',
            'items-per-page-options': [10, 30, 40, 50]
        }"
        item-key="title"
        must-sort
        :sort-by="['title']"
        :sort-desc="[false]"
    >
        <template v-slot:item="{ item }">
            <tr class="table-row" style="border-left: 2px solid black"  >
                <td style="width:300px;">
                    <v-tooltip bottom>
                        <template v-slot:activator="{ on, attrs }">
                            <span class="title-box" v-bind="attrs" v-on="on" style="line-height: 45px"><strong> {{ item.title }} </strong></span>
                        </template>
                    </v-tooltip>
                </td>
                <td >
                    <v-chip class="ma-1" small dark>{{item.jo_title.split('(')[0]}}</v-chip><br/>
                    <v-chip class="ma-1" small outlined>{{item.jo_title.split('(')[1].slice(0,-1)}}</v-chip>
                </td>
                <td class="jo-contents-box">{{ item.jo_contents }}</td>
                <td >
                    <v-chip small outlined class="ma-1" v-for="age,key in item.age_list" :key="key">{{age}}</v-chip>
                    </td>
            </tr>
        </template>
                                    
    </v-data-table>
</v-card>
</template>
<script>

export default ({
    data() {
        return{
            search: ''
        }
        
    },
    mounted(){
    },
    computed:{
        headers(){
            return [{
                text: '법령명',
                align: 'start',
                sortable: true,
                value: 'title',
            },
            {
                text: '조문제목',
                align: 'start',
                sortable: false,
                value: 'jo_title',
            },
            {
                text: '조문내용',
                align: 'start',
                sortable: false,
                value: 'jo_contents',
            },
            {
                text: '나이',
                align: 'start',
                sortable: true,
                value: 'age_list',
            },
            ]
        },
        lawData(){
            return this.$store.state.lawData;
        }
    }
})
</script>
<style scoped>

@media (max-width: 568px) {
    .jo-contents-box{
        display: none;
    }

}
</style>
