<template>
  <section class="py-[200px] flex flex-col items-center justify-center px-4">
    <div class="text-[32px] font-semibold text-dark mb-4">Select Companies</div>
    <div class="w-full card">
      <div class="form-group">
        <label for="" class="text-grey">Companies</label>
        <p v-if="$fetchState.pending">Fetching Companies...</p>
        <select v-else name="companies" class="appearance-none input-field form-icon-chevron_down"
          v-model="selectedCompany">
          <option :value="company.id" v-for="company in companies.data.result.data">
            {{ company.name }}
          </option>
        </select>
      </div>
      <div class="grid md:grid-cols-2 gap-2 sm:grid-cols-1">
        <button @click="openCompany" type="button" class="w-full btn btn-primary mt-[14px]">
          Continue
        </button>
        <NuxtLink :to="{name: 'companies-create'}" class="w-full btn bg-gray-400 text-white mt-[14px]">
          create
        </NuxtLink>
      </div>

    </div>
  </section>
</template>
<script>
export default {
  middleware: 'auth',
  data() {
    return {
      companies: [],
      selectedCompany: '',
    }
  },
  async fetch() {
    this.companies = await this.$axios.get('/company')
  },
  methods: {
    openCompany() {
      console.log(this.selectedCompany);
      this.$router.push({
        name: 'companies-id',
        params: {
          id: this.selectedCompany
        }
      })
    },
  }
}
</script>
  