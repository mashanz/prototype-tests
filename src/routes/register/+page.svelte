<main class="flex h-screen w-full bg-gray-100">
	<div class="m-auto w-full">
		<form action="" class="flex flex-col max-w-xl m-auto p-3 border bg-white">
			<h1 class="font-bold text-center text-xl">REGISTER</h1>
			<label for="role">Role</label>
			<div class="flex gap-2">
				<div class="flex-grow p-3 border bg-white">
					<input type="radio" name="role" value="client" id="client" required />
					<label class="w-full" for="client">Join as a Client</label>
				</div>
				<div class="flex-grow p-3 border bg-white">
					<input type="radio" name="role" value="freelancer" id="freelancer" required />
					<label class="w-full" for="freelancer">Join as a Freelancer</label>
				</div>
			</div>
			<label for="email">Email</label>
			<input class="p-3 border" type="email" name="email" placeholder="Email" required />
			<label for="password">Password</label>
			<input class="p-3 border" type="password" name="password" placeholder="Password" required />
			<label for="password2">Re-type Password</label>
			<input
				class="p-3 border"
				type="password"
				name="password2"
				placeholder="Re-type Password"
				required />
			<button class="bg-blue-500 text-white p-3 my-2" type="submit">Register</button>
		</form>
	</div>
</main>
