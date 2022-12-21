<template>
	<div id="app">
		<p><strong>Add a new contact:</strong></p>
		<div>
			<label
				>First Name: <input type="text" class="userFirstname" v-model="firstName"
			/></label>
			<br />
			<label
				>Last Name: <input type="text" class="userLastname" v-model="lastName"
			/></label>
			<br />
			<label>Phone: <input type="number" class="userPhone" v-model="phone" /></label>
			<br />
			<button class="submitButton" @click="addContact">Add New Contact</button>
		</div>
		<table id="phoneBookItems" class="informationTable">
			<thead>
				<th class="cell">Last Name</th>
				<th class="cell">First Name</th>
				<th class="cell">Phone</th>
			</thead>
			<tbody>
				<tr v-for="item in items" :key="item.id">
					<td class="cell-item">{{ item.lastName }}</td>
					<td class="cell-item">{{ item.firstName }}</td>
					<td class="cell-item">{{ item.phone }}</td>
				</tr>
			</tbody>
		</table>
	</div>
</template>

<script>
	export default {
		name: 'App',
		data() {
			return {
				items: [],
				firstName: 'Coder',
				lastName: 'Byte',
				phone: '8885559999',
			};
		},
		methods: {
			addContact() {
				const contact = {
					id: Date.now(),
					firstName: this.firstName,
					lastName: this.lastName,
					phone: this.phone,
				};
				// const contacts = [...this.items, contact?]
				this.items.push(contact);
				const sortArray = (x, y) => x.lastName.localeCompare(y.lastName);

				this.items = this.items.sort(sortArray);
				this.firstName = '';
				this.lastName = '';
				this.phone = '';
			},
		},
	};
</script>

<style>
	* {
		font-family: arial, sans-serif;
	}
	body {
		width: 90%;
		margin: 0 auto;
	}
	input {
		padding: 5px 10px;
		margin-bottom: 10px;
		border-radius: 5px;
		border: 0.5px solid #ccc;
	}
	button {
		padding: 10px 20px;
		border: none;
		border-radius: 5px;
		background-color: #0080ff;
		color: #fff;
		font-weight: bold;
		margin-bottom: 40px;
	}
	button:hover {
		background-color: #004c99;
		cursor: pointer;
	}
	#phoneBookItems {
		max-width: 450px;
	}
	.cell,
	cell-item {
		min-width: 100px;
		width: 33%;
	}
	.cell {
		font-size: 14px;
	}
	.cell-item {
		padding: 5px;
		text-align: center;
	}
</style>
