<template>
  <div id="app">
    <ul>
      <li><a href="" class="selected" @click.prevent="ticketRank(movies), select($event)">예매순</a></li>
      <li><a href="" @click.prevent="scoreRank(movies), select($event)">평점순</a></li>
      <li><a href="" @click.prevent="openDateRank(movies), select($event)">개봉일순</a></li>
      <li><a href="" @click.prevent="weekRank(movies), select($event)">주말관객순</a></li>
      <li><a href="" @click.prevent="saleRank(movies), select($event)">다운로드순</a></li>
    </ul>
    <MovieList
      :rateMach="rateMach"
      :movies="movies"
    ></MovieList>
  </div>
</template>

<script>
import MovieList from './components/MovieList.vue'

export default {
  name: 'App',
  components: {
    MovieList
  },
  data() {
    return {
      rateMach: {
        0: '전체관람가',
        12: '12세이상 관람가',
        15: '15세이상 관람가',
        19: '19세이상 관람가',
        20: '청소년관람불가'
      },
      movies: [
        {
          name: '남애의 여름밤',
          src: 'images/mov_1.jpg',
          rate: 15,
          score: 9.43, //평점
          sale: 11.7,  //판매율
          openDate: 8.26,  //개봉일
          ticketing: 11.79, //예매율
          week: 8777, //주말관객
        },
        {
          name: '시크릿 가든',
          src: 'images/mov_2.jpg',
          rate: 0,
          score: 8.13,
          sale: 7.7,  //판매율
          openDate: 9.3,  //개봉일
          ticketing: 20.66,
          week: 2000
        },
        {
          name: '반도',
          src: 'images/mov_3.jpg',
          rate: 15,
          score: 8.54,
          sale: 7.7,
          openDate: 9.3,
          ticketing: 9.79,
          week: 23327
        },
        {
          name: '강철비2',
          src: 'images/mov_4.jpg',
          rate: 19,
          score: 7.43,
          sale: 7.7,
          openDate: 9.7,
          ticketing: 8.6,
          week: 23421
        },
        {
          name: '신혼여행 허리케인',
          src: 'images/mov_5.jpg',
          rate: 12,
          score: 6.2,
          sale: 10.7,
          openDate: 8.17,
          ticketing: 2.11,
          week: 3213
        },
        {
          name: '테넷',
          src: 'images/mov_6.jpg',
          rate: 19,
          score: 7.12,
          sale: 9.11,
          openDate: 11.17,
          ticketing: 3.21,
          week: 3213
        },
        {
          name: '오케이 마담',
          src: 'images/mov_7.jpg',
          rate: 20,
          score: 9.43,
          sale: 9.11,
          openDate: 9.1,
          ticketing: 3.79,
          week: 2277
        },
        {
          name: '다만 악에서 구하소서',
          src: 'images/mov_8.jpg',
          rate: 20,
          score: 8.9,
          sale: 8.8,
          openDate: 8.21,
          ticketing: 12.79,
          week: 83777
        }
      ]
    }
  },
  methods: {
    ticketRank(movies) {
      movies.sort((a, b) => {
        return b.ticketing - a.ticketing
      })
    },
    scoreRank(movies) {
      movies.sort((a, b) => {
        return b.score - a.score 
      })
    },
    openDateRank(movies) {
      movies.sort((a, b) => {
        return b.openDate - a.openDate 
      })
    },
    weekRank(movies) {
      movies.sort((a, b) => {
        return b.week - a.week 
      })
    },
    saleRank(movies) {
      movies.sort((a, b) => {
        return b.sale - a.sale 
      })
    },
    select(event) {
      const liEls = event.target.parentNode.parentNode.children;
      for (let i=0; i<liEls.length; i++) {
        liEls[i].children[0].classList.remove('selected')
      }
      event.target.className = 'selected';
    }
  },
  created() {
    this.movies.sort((a, b) => {
      return b.ticketing - a.ticketing
    })
  }
}
</script>

<style>
  @charset 'utf-8';

/* reset */
body {
	font:normal 12px Arial, sans-serif;
	line-height:1.3;
	color:#666666;
	background-color:#fff;
	margin:0;
	padding:0;
}
h1, h2, h3, h4, h5, h6 {font-size:1em;}
h1, h2, h3, h4, h5, h6, div, p, dl, dt, dd, ul, ol, li, form, fieldset, blockquote, address, table, thead, tbody, tfoot, tr, td, caption {
	margin:0;
	padding:0;
}
li {list-style:none;}
a {text-decoration:none; color:white}
body {background-color:#242424; }
ul {
  display: flex;
  justify-content: center;
  align-items: center;
}
ul li {
  padding: 20px 13px 0px 21px;
  font-size: 16px;
}
ul li a.selected {
  color: red;
}
</style>
