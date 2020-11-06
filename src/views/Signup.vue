<template>
	
	<div class="container">
		<h1>Signup</h1>
		<div class="row">
			<div class="col-sm">
				<h5 style="margin-bottom:2em; opacity:.7;">No account yet? No problem, create one now by filling the fields.</h5>
			</div>
		</div>
		<div class="row">
			<div class="col-sm"></div>
			<div class="col-sm" style=" min-width:fit-content;">
			<form style="margin-bottom:2em;">
				<div class="form-group">
					<label for="exampleInputEmail1">Name</label>
					<input type="name" class="form-control" id="exampleInputName" placeholder="First Name" required>
					<!-- <small id="emailHelp" class="form-text text-muted"></small> -->
				</div>
				<div class="form-group">
					<label for="exampleInputEmail1">Surname</label>
					<input type="surname" class="form-control" id="exampleInputSurname" placeholder="Last Name" required>
				</div>
				<div class="form-group">
					<label for="exampleInputEmail1">Mail</label>
					<input type="email" class="form-control" id="exampleInputEmail1" aria-describedby="emailHelp" placeholder="Enter email" required>
					<!-- <small id="emailHelp" class="form-text text-muted">Your info is in safe hands.</small> -->
				</div>
				<div class="form-group">
					<label for="exampleInputEmail1">Phone Number</label>
					<input type="tel" class="form-control" id="tel" placeholder="Phone Number">
					<small id="emailHelp" class="form-text text-muted">Your number is optional, but it provides extra security.</small>
				</div>
				<div class="form-group">
					<label for="exampleInputPassword1">Password</label>
					<input type="password" class="form-control" id="exampleInputPassword1" placeholder="Password" required>
				</div>
				<div class="form-group">
					<label for="exampleInputPassword2">Repeat password</label>
					<input type="password" class="form-control" id="exampleInputPassword2" placeholder="Repeat Password" required>
				</div>
				<div class="form-check">
					<input type="checkbox" class="form-check-input" id="exampleCheck1" required>
					<small class="form-check-label" for="exampleCheck1">I like your info stealing policy and I accept.</small>
				</div>
				<button type="submit" class="btn btn-primary">Submit</button>
				</form>
			</div>
			<div class="col-sm"></div>
		</div>
	</div>
</template>


<style lang="scss">
	.form-check{
		margin: 2em 0 1em 0;
	}
</style>