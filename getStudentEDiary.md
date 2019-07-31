**getStudentEDiary**
----
	Returns student eDiary events available to a particular student.
	
* **Version History:**

	TASS v51.2 - Method Added

* **Version:**

	2

* **Method:**

	`GET | POST`
	
*  **Params:**

	**Required:**

	`studcode [string]` - student code.

	`start_date [date dd/mm/yyyy]` - start date.

	**Optional:**

	`feedcode [string]` - a list of student's eDiary codes or just one code.

	`end_date [date dd/mm/yyyy]` - Defaults to `start_date` if not supplied.

	**Conditional:**
	
	none

* **Success Response:**

	```javascript
	{
		"calendar": [
			{
				"location": "",
				"attachment": {
					"deep_link": "",
					"file_name": ""
				},
				"url_text": "",
				"day_time_desc": "Wed 16 Jan 2019 at 9:00am (End 3:00pm)",
				"campus_code": "",
				"dayFlag": "",
				"summary": "Rippers Day Holiday",
				"has_attachment": false,
				"description": "Rippers Day Holiday",
				"single_day": true,
				"year_groups": {
					"0": "P",
					"1": 1,
					"2": 2,
					"3": 3,
					"4": 4,
					"5": 5,
					"6": 6,
					"7": 7,
					"8": 8,
					"9": 9,
					"10": 10,
					"11": 11,
					"12": 12,
					"-1": "PK",
					"-2": "AA"
				},
				"source": "school",
				"title": "Rippers Day",
				"start": "2019-01-16 09:00:00",
				"end": "2019-01-16 15:00:00",
				"id": 7747,
				"url_link": "",
				"feed": "School and Teacher Calendar",
				"all_day": false
			},
			{
				"location": "Library",
				"attachment": {},
				"url_text": "",
				"day_time_desc": "",
				"summary": "Mr J Sheather in Library",
				"description": "Pastoral Care: ASSEMBLY 11.A with Mr J Sheather",
				"has_attachment": false,
				"single_day": true,
				"source": "timetable",
				"start": "2019-01-07 08:00:00",
				"end": "2019-01-07 09:29:00",
				"title": "ASSEMBLY",
				"id": "timetable_87_ASSEMBLY_1_1_11|A_class",
				"url_link": "",
				"all_day": false,
				"feed": "My Timetable"
			},
			{
				"location": "",
				"attachment": {},
				"deep_link": "{\"target\":\"curricular.activity\",\"studcode\":\"0009130\",\"activity_assign_id\":\"4645\",\"prod_menu\":\"N\"}",
				"url_text": "Go to this activity.",
				"day_time_desc": "",
				"summary": "Modern History 11 A\nActivity Available From: Tue 29 Jan 2019 at 03:17 PM",
				"description": "Modern History 11 A\nActivity Available From: Tue 29 Jan 2019 at 03:17 PM",
				"has_attachment": false,
				"single_day": true,
				"source": "activity",
				"start": "2019-01-29 15:17:00",
				"end": "",
				"title": "Gus Grissom - the first man to fly in space twice.",
				"id": "activity-0009130-F099A718-E987-9D21-9C9CE293A07CB16B-4645",
				"url_link": "",
				"all_day": false,
				"feed": "LMS / Assessment Activities"
			}
		]
	}
	```
 
* **Error Response:**

	`[stud_code]` does not have permission to access eDiary
	```javascript
	"__status": "invalid",
	"__msg": "The teacher([stud_code]) has no permission for My Calendar(eDiary).",
	"__invalid": {}
	```

	`[required_field_name]` not supplied
	```javascript
	__invalid: {
		"[required_field_name]": "field is required"
	}
	```

	`studcode` does not exist
	```javascript
	__invalid: {
		"studcode": "[studcode] does not exist."
	}
	```

	`studcode` is not a current student
	```javascript
	__invalid: {
		"studcode": "[studcode] is not a current student."
	}
	```

	`start_date` is not in correct date format
	```javascript
	__invalid: {
		"start_date": "Value is not a valid date."
	}
	```

	`end_date` is not in correct date format
	```javascript
	__invalid: {
		"end_date": "Value is not a valid date."
	}
	```

	`end_date` is earilier than `start_date`
	```javascript
	__invalid: {
		"enddate": "end date cannot be earlier than start date."
	}
	```

	`feedcode` is not a valid code
	```javascript
	__invalid: {
		"feedcode": "[feedcode] is not a valid feedcode."
	}
	```

* **Sample Parameters:**

	```javascript
		{
			"studcode":"0009130",
			"start_date":"2018-05-01",
			"end_date":"2019-05-01",
			"feedcode":"per,sch,tt,act,tour,pti,sport,brd,pcare"
		}
	```

* **Sample GET:** (With URL Encoded `token`)

	```HTML
	http://api.tasscloud.com.au/tassweb/api/?method=getStudentEDiary&appcode=API19&company=10&v=2&token=PQty00DXnXem4ZMp428A%2FwD6a5TB7HUYMta3sKtv89XwPsa%2FeB2RtUrAA5%2FWSxTA%2F%2Bm30VOCYMahvOVWTkTOmFJKzT8N67mvjRyULtu51I4%3D
	```
	
* **Sample POST:**

	```HTML
	<form id="postForm" name="postForm" method="POST" action="http://api.tasscloud.com.au/tassweb/api/">
		 <input type="hidden" name="method" value="getStudentEDiary">
		 <input type="hidden" name="appcode" value="API19">
		 <input type="hidden" name="company" value="10">
		 <input type="hidden" name="v" value="2">
		 <textarea name="token">PQty00DXnXem4ZMp428A/wD6a5TB7HUYMta3sKtv89XwPsa/eB2RtUrAA5/WSxTA/+m30VOCYMahvOVWTkTOmFJKzT8N67mvjRyULtu51I4=</textarea>
	</form>
	```
