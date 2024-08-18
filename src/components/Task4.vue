<template>
    <div>
        <v-container>
          <div>
            <v-label>Рядки: <input v-model.number="rows" type="number" min="1" border="1"/></v-label>
            <v-label>Стовпці: <input v-model.number="cols" type="number" min="1"/></v-label>
            
            <table border="1px">
              <tr v-for="row in rows" :key="row">
                <td style="border: 1px solid black;" v-for="col in cols" :key="col">({{ row }}, {{ col }})</td>
              </tr>
            </table>
          </div>
          <div>
            <ul>
              <li v-for="(ticket, index) in tickets" :key="index">
                {{ ticket.name }}
                <ul>
                  <li v-for="(number, subIndex) in ticket.numbers" :key="subIndex">
                    {{ number }}
                  </li>
                </ul>
              </li>
            </ul>            
          </div>
          <div>
            <ul>
              <li v-for="(item, index) in paginatedItems" :key="index">{{ item }}</li>
            </ul>
            <button @click="prevPage" :disabled="currentPage === 1">Prev</button>
            <span style="margin: 10px;">{{ currentPage }}</span>
            <button @click="nextPage" :disabled="currentPage === totalPages">Next</button>
          </div>
          <div>
            <v-label>Filtered value <input v-model="filterNumber" placeholder="Filter by number in ticket" type="number"/> </v-label>
            <ul>
              <div v-for="(ticket, index) in tickets" :key="index">
                <li v-if="isValidTicket(ticket)">
                  {{ ticket.name }}
                  <ul>
                    <li v-for="(number, subIndex) in ticket.numbers" :key="subIndex">
                      {{ number }}
                    </li>
                  </ul>
                </li>
            </div>
            </ul>
          </div> 
       </v-container>
    </div>
  </template>
  
<script>
  export default {
    data() {
      return {
        rows: 1,
        cols: 1,
        tickets: [
          { name: 'Ticket 1', numbers: [2,46,17,32,57,16] },
          { name: 'Ticket 2', numbers: [5,46,28,67,92,12] },
          { name: 'Ticket 3', numbers: [44,5,17,26,62,24] },
          { name: 'Ticket 4', numbers: [3,12,46,7,15,8] },
          { name: 'Ticket 5', numbers: [53,42,86,84,62,30] },
        ],
        items: [],
        currentPage: 1,
        itemsPerPage: 10,
        filterNumber: 0,                
      };
    },
    methods: {
      prevPage() {
        if (this.currentPage > 1) {
          this.currentPage--;
        }
      },
      nextPage() {
        if (this.currentPage < this.totalPages) {
          this.currentPage++;
        }
      },
      isValidTicket(ticket) {
        if (this.filterNumber === 0) {
          return true;
        }
        return ticket.numbers.includes(this.filterNumber);
      },      
    },
    computed: {
      totalPages() {
        return Math.ceil(this.items.length / this.itemsPerPage);
      },
      paginatedItems() {
        const start = (this.currentPage - 1) * this.itemsPerPage;
        const end = start + this.itemsPerPage;
        return this.items.slice(start, end);
      },
    },    
    mounted() {
      for (let i = 0; i < 50; i++) {
        this.items.push('Element ' + (i + 1));
      }
    }
  };
</script>

