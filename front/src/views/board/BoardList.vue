<template>
  <div class="board-list">
    <div class="common-buttons">
      <button type="button" class="w3-button w3-round w3-blue-gray" v-on:click="fnWrite">등록</button>
    </div>
    <table class="w3-table-all">
      <thead>
      <tr>
        <th>No</th>
        <th>제목</th>
        <th>작성자</th>
        <th>등록일</th>
      </tr>
      </thead>
      <tbody>
      <tr v-for="(row, idx) in list" :key="idx">
        <td>{{row.idx}}</td>
        <td><a v-on:click="fnView(`${row.idx}`)">{{row.title}}</a></td>
        <td>{{row.author}}</td>
        <td>{{row.created_at}}</td>
      </tr>
      </tbody>
    </table>
    <div class="pagination w3-bar w3-padding-16 w3-small" v-if="paging.total_list_cnt > 0">
      <span class="pg">
        <a href="javascript:;" @click="fnPage(1)" class="first w3-button w3-border">@lt;@lt;</a>
        <a href="javascript:;" v-if="paging.start_page > 10" @click="fnPage(`${paging.start_page
        }`)" class="first w3-button w3-border">@lt;@lt;</a>
      </span>
    </div>
  </div>
</template>
<script>
  export default {
    data() {
      return {
        requestBody: {},
        list: {},
        paging: {
          block: 0,
          end_page: 0,
          next_block: 0,
          page: 0,
          page_size: 0,
          prev_block: 0,
          start_index: 0,
          start_page: 0,
          total_block_cnt: 0,
          total_list_cnt: 0,
          total_page_cnt: 0,
        },
        page: this.$route.query.page ? this.$route.query.page :1,
        size: this.$route.query.size ? this.$route.query.size : 10,
        keyword: this.$route.query.keyword,
        pageNavigation: function () {
          let pageNumber = [];
          let start_page = this.paging.start_page;
          let end_page = this.paging.end_page;
          for (let i = start_page; i <= end_page; i++) pageNumber.push(i);
          return pageNumber;
        }
      }
    },
    mounted() {
      this.fnGetList()
    },
    methods: {
      fnGetList() {
        this.list = [
          {
            "idx":1,
            "title": "제목1",
            "author": "작성자1",
            "created_at": "작성일시1"
          },
          {
            "idx":1,
            "title": "제목1",
            "author": "작성자1",
            "created_at": "작성일시1"
          },
          {
            "idx":1,
            "title": "제목1",
            "author": "작성자1",
            "created_at": "작성일시1"
          }
        ]
      }
    }
  }
</script>