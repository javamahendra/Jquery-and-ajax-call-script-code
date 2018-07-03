# Jquery-and-ajax-call-script-code


<script type="text/javascript">
+	$(document).ready(function() {
+		$("#btnDelete").click(deleteEmpRecord);
+	});
+	function deleteEmpRecord() {
+
+		$.ajax({
+			type : 'DELETE',
+			url : 'http://localhost:8002/RESTDBLab1/rest/emp/employee/'+ $('#deleteId').val(),
+			success : function(data) {
+				alert('Employee Record deleted successfully');
+			},
+			error : function(jqXHR, textStatus, errorThrown) {
+				alert('Employee Record error');
+			}
+		});
+	}
+</script>
+
+<body>
+
+
+	<input id="deleteId" name="id" type="text" />
+
+	<button id="btnDelete">Delete</button>
+
+
+</body>

------------------------------------------------

<script type="text/javascript">
+	$(document).ready(function() {
+		$("#btnSubmit").click(addEmpRecord);
+
+	});
+	function addEmpRecord() {
+
+		$.ajax({
+			type : 'POST',
+			contentType : 'application/json',
+			url : 'http://localhost:8002/RESTDBLab1/rest/emp/employee/',
+			dataType : "json",
+			data : formToJSON(),
+			success : function(data) {
+				alert('Employee Record inserted successfully');
+				console.log(data);
+			},
+			error : function(jqXHR, textStatus, errorThrown) {
+				alert('Employee Record error');
+			}
+		});
+	}
+
+	function formToJSON() {
+
+		return JSON.stringify({
+
+			"name" : $('#empName').val(),
+			"designation" : $('#empDesignation').val(),
+			"salary" : $('#empSalary').val(),
+			"address" : {
+				"doorno" : $('#empDoorno').val(),
+				"street" : $('#empStreet').val(),
+				"location" : $('#empLocation').val(),
+				"city" : $('#empCity').val()
+			}
+		});
+		
+
+	}
+</script>
+
+<body>
+
+
+	Name:
+	<input id="empName" name="id" type="text" />
+	<br /> Designation:
+	<input id="empDesignation" name="design" type="text" />
+	<br /> Salary:
+	<input id="empSalary" name="sal" type="text" />
+	<br /> Door Number:
+	<input id="empDoorno" name="doorNo" type="text" />
+	<br /> Street:
+	<input id="empStreet" name="street" type="text" />
+	<br /> Location:
+	<input id="empLocation" name="loc" type="text" />
+	<br /> City:
+	<input id="empCity" name="city" type="text" />
+	<br />
+
+
+	<button id="btnSubmit">Submit</button>
+
+</body>

----------------------------------------------------

<script type="text/javascript">
+	$.ajax({
+		type : 'GET',
+		url : 'http://localhost:8002/RESTDBLab1/rest/emp/employee/',
+
+		dataType : 'json',
+
+		success : function(data) {
+
+			drawTable(data);
+		}
+	});
+	function drawTable(data) {
+		for (var i = 0; i < data.length; i++) {
+
+			var row = $("<tr />")
+			console.log(data[i]);
+			$("#personDataTable").append(row); //this will append tr element to table... keep its reference for a while since we will add cels into it
+			row.append($("<td>" + data[i].id + "</td>"));
+			row.append($("<td>" + data[i].name + "</td>"));
+			row.append($("<td>" + data[i].designation + "</td>"));
+			row.append($("<td>" + data[i].salary + "</td>"));
+			row.append($("<td>" + data[i].address.doorno + "</td>"));
+			row.append($("<td>" + data[i].address.street + "</td>"));
+			row.append($("<td>" + data[i].address.location + "</td>"));
+			row.append($("<td>" + data[i].address.city + "</td>"));
+		}
+	}
+</script>
+
+<body>
+
+	<table id="personDataTable" border="10px">
+		<tr>
+			<th>Id</th>
+			<th>Name</th>
+			<th>Designation</th>
+			<th>Salary</th>
+			<th>doorno</th>
+			<th>street</th>
+			<th>location</th>
+			<th>city</th>
+		</tr>
+	</table>
+
+
+</body>
+</html> 
 
-----------------------------------------------------------

+<script type="text/javascript">
+	$(document).ready(function() {
+		$("#btnSubmit").click(viewEmpList);
+	});
+	function viewEmpList() {
+
+		$.ajax({
+			type : 'GET',
+
+			url : 'http://localhost:8002/RESTDBLab1/rest/emp/employee/'
+					+ $('#viewId').val(),
+
+			dataType : 'json',
+
+			success : function(data) {
+				drawTable(data);
+
+			},
+			error : function(jqXHR, textStatus, errorThrown) {
+				alert('Employee Record error');
+			}
+		});
+	}
+	function drawTable(data) {
+		for (var i = 0; i < data.length; i++) {
+
+			var row = $("<tr />")
+			console.log('alert inside drawtable');
+			console.log(data[i]);
+			$("#empDataTable").append(row);
+			row.append($("<td>" + data[i].id + "</td>"));
+			row.append($("<td>" + data[i].name + "</td>"));
+			row.append($("<td>" + data[i].designation + "</td>"));
+			row.append($("<td>" + data[i].salary + "</td>"));
+			row.append($("<td>" + data[i].address.doorno + "</td>"));
+			row.append($("<td>" + data[i].address.street + "</td>"));
+			row.append($("<td>" + data[i].address.location + "</td>"));
+			row.append($("<td>" + data[i].address.city + "</td>"));
+		}
+	}
+	$(document).ready(function() {
+		$('#btnRefresh').click(function() {
+			location.reload();
+		});
+	});
+</script>
+
+<body>
+
+
+	<input id="viewId" name="id" type="text" />
+
+
+	<button id="btnSubmit">Submit</button>
+
+
+	<br />
+	<br />
+
+
+	<table id="empDataTable" border="10px">
+		<tr>
+			<th>Id</th>
+			<th>Name</th>
+			<th>Designation</th>
+			<th>Salary</th>
+			<th>doorno</th>
+			<th>street</th>
+			<th>location</th>
+			<th>city</th>
+		</tr>
+	</table>
+	<br />
+	<button id="btnRefresh">Refresh</button>
+
+</body>

----------------------------------------------------

<script type="text/javascript">
+	$(document).ready(function() {
+		$("#btnUpdate").click(updateEmpRecord);
+	});
+
+	function updateEmpRecord() {
+
+		$.ajax({
+			type : 'PUT',
+			url : 'http://localhost:8002/RESTDBLab1/rest/emp/employee/'
+					+ $('#viewId').val(),
+			dataType : "json",
+			data : formToJSON(),
+			success : function(data) {
+
+				alert(updatedone);
+			}
+		});
+	}
+
+	function formToJSON() {
+
+		return JSON.stringify({
+
+			"name" : $('#empName').val(),
+			"designation" : $('#empDesignation').val(),
+			"salary" : $('#empSalary').val(),
+			"address" : {
+				"doorno" : $('#empDoorno').val(),
+				"street" : $('#empStreet').val(),
+				"location" : $('#empLocation').val(),
+				"city" : $('#empCity').val()
+			}
+		});
+
+	}
+</script>
+
+<body>
+
+	Enter the Id
+	<input id="viewId" name="id" type="text" />
+	<br /> Name:
+	<input id="empName" name="id" type="text" />
+	<br /> Designation:
+	<input id="empDesignation" name="design" type="text" />
+	<br /> Salary:
+	<input id="empSalary" name="sal" type="text" />
+	<br /> Door Number:
+	<input id="empDoorno" name="doorNo" type="text" />
+	<br /> Street:
+	<input id="empStreet" name="street" type="text" />
+	<br /> Location:
+	<input id="empLocation" name="loc" type="text" />
+	<br /> City:
+	<input id="empCity" name="city" type="text" />
+	<br />
+
+
+	<button id="btnUpdate">Update</button>
+
+
+</body>

-----------------------------------------
