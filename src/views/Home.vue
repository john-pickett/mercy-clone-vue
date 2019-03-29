<!-- eslint-disable -->
<template>
	<v-container grid-list-sm>
		<h2>New Cases</h2>
		<v-layout row wrap>
			<v-flex md3 v-for="item in allCases" :key="item">
				<v-card>
					<v-card-title primary-title>
						<h3 class="headline mb-0">{{item.u_patient_name}}</h3>
					</v-card-title>
					<v-card-title>
						<p>Lorem ipsum dolor sit amet, brute iriure accusata ne mea. Eos suavitate referrentur ad, te duo agam libris qualisque, utroque quaestio accommodare no qui. Et percipit laboramus usu, no invidunt verterem nominati mel. Dolorem ancillae an mei, ut putant invenire splendide mel, ea nec propriae adipisci. Ignota salutandi accusamus in sed, et per malis fuisset, qui id ludus appareat.</p>
					</v-card-title>
					<v-card-actions>
						<v-btn depressed color="orange">View</v-btn>
						<v-btn depressed color="orange">Work Case</v-btn>
					</v-card-actions>
				</v-card>
			</v-flex>
  		</v-layout>
		  <p>&nbsp;</p>
		  <v-divider></v-divider>
		  <h2>Working Cases</h2>
	</v-container>
	
</template>

<script lang="ts">
/* eslint-disable */
import Vue from 'vue';
import axios from 'axios';
// import HelloWorld from '@/components/HelloWorld.vue'; // @ is an alias to /src

export default Vue.extend({
	data: () => ({
		allCases: [],
		wipCases: []
		
	}),
	methods: {
		loadCaseData () {
			console.log('loading data')
			axios.get('https://dev54390.service-now.com/api/now/table/u_call_logs', {
				auth: {
					username: 'admin',
					password: 'jAi4WmRD0zKa'
				}
			}).then((res) => {
				this.allCases = res.data.result
			})
		}
	},
	created () {
		this.loadCaseData()
	}

});
</script>
 