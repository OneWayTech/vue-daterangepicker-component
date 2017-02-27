<template>
  <div class="btn btn-default pos-rel p-0 -date-range">
    <i class="glyphicon glyphicon-calendar"></i>
    <input class="cursor-pointer" readonly
      v-el:drp placeholder="Select a date range...">
  </div>
</template>
<script>
import updateQuery from 'vue-update-query-mixin'
import { default as defaultRange, FORMAT } from './defaultRange'

export default {
  mixins: [updateQuery],
  props: {
    // more options see http://www.daterangepicker.com/#options
    config: { type: Object, default: () => ({}) }
  },
  computed: {
    startDate () {
      if (!this) return // TypeError: Cannot read property '$route' of null
      return this.$route.query.startDate || defaultRange.startDate
    },
    endDate () {
      if (!this) return
      return this.$route.query.endDate || defaultRange.endDate
    }
  },
  attached() {
    $(this.$els.drp).daterangepicker({
      locale: { format: FORMAT },
      autoUpdateInput: true,
      showDropdowns: true,
      opens: 'center',
      ranges: {
        'Last 7 days': [
          moment().subtract(6, 'days').startOf('day'),
          moment().endOf('day')
        ],
        'Last 15 days': [
          moment().subtract(14, 'days').startOf('day'),
          moment().endOf('day')
        ],
        'Last 30 days': [
          moment().subtract(29, 'days').startOf('day'),
          moment().endOf('day')
        ],
        'This month': [
          moment().startOf('month'),
          moment().endOf('month')
        ],
        'Last Month': [
          moment().subtract(1, 'month').startOf('month'),
          moment().subtract(1, 'month').endOf('month')
        ]
      },
      startDate: this.startDate,
      endDate: this.endDate,
      ...this.config
    })
    .on('apply.daterangepicker', (e, { startDate, endDate }) => {
      this.updateQuery({
        startDate: startDate.format(FORMAT),
        endDate: endDate.format(FORMAT)
      })
    })
  }
}
</script>
<style scoped>
.pos-rel {
  position: relative;
}
.p-0 {
  padding: 0;
}
.cursor-pointer {
  cursor: pointer;
}
.-date-range > i {
  position: absolute;
  top: 13px;
  left: 15px;
  pointer-events: none;
}
.-date-range > input {
  border: none;
  background-color: transparent;
  padding: 10px 15px 10px 35px;
  min-width: 240px;
}
</style>
