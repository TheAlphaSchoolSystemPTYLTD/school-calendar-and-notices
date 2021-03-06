**getTeacherEDiary**
----
	Returns teacher eDiary events available to a particular teacher.
	
* **Version History:**

	TASS v51.2 - Method Added

* **Version:**

	2

* **Method:**

	`GET | POST`
	
*  **Params:**

	**Required:**

	`tchcode [string]` - teacher code.

	`start_date [date dd/mm/yyyy]` - start date.

	**Optional:**

	`feedcode [string]` - a list of teacher's eDiary codes or just one code.

	`end_date [date dd/mm/yyyy]` - Defaults to `start_date` if not supplied.

	**Conditional:**
	
	none

* **Success Response:**

	```javascript
		{
			"calendar": [
						{
							"location": "I Block - Room 7",
							"attachment": {
										"deep_link": "",
										"file_name": ""
							},
							"url_text": "",
							"day_time_desc": "Thu 21 Mar 2019 at 12:00am (End 12:00am)",
							"campus_code": "",
							"dayFlag": "",
							"summary": "All Welcome",
							"has_attachment": false,
							"description": "All Welcome",
							"single_day": true,
							"year_groups": {
											"0": "P"
							},
							"source": "school",
							"title": "Trivia Night",
							"start": "2019-03-21 00:00:00",
							"end": "2019-03-21 00:00:00",
							"id": 7863,
							"url_link": "",
							"feed": "School and Teacher Calendar",
							"all_day": true
						},
						{
							"location": "Art Room",
							"attachment": {
										"file_size": 4076,
										"deep_link": "{\"target\":\"calendar.attachment\",\"feedcode\":\"tsch\",\"event_id\":\"7788\",\"event_type\":\"school\"}",
										"file_name": "TheerrormessagewordingforinsertaduplicatedIDMrecord.PNG"
							},
							"url_text": "http://www.apitesting.com.au",
							"day_time_desc": "Fri 15 Feb 2019 at 12:00am (End 12:00am)",
							"campus_code": "SE",
							"dayFlag": "",
							"summary": "API testing Event Desc.",
							"has_attachment": true,
							"description": "API testing Event Desc.",
							"single_day": true,
							"year_groups": {
											"11": 11
							},
							"source": "school",
							"title": "API testing Event Name",
							"start": "2019-02-15 00:00:00",
							"end": "2019-02-15 00:00:00",
							"id": 7788,
							"url_link": "http://www.apitesting.com.au",
							"feed": "School and Teacher Calendar",
							"all_day": true
						}
			],
			"__tassversion": "01.053.3.000",
			"token": {
						"tchcode": "AJ",
						"feedcode": "per,sch,tt,act,tour,pti",
						"timestamp": "{ts '2021-01-25 10:15:37'}",
						"end_date": "2019-05-01",
						"start_date": "2018-05-01"
			}
		}
	```
 
* **Error Response:**

	`[tch_code]` does not have permission to access eDiary
	```javascript
	"__status": "invalid",
	"__msg": "The teacher([tch_code]) has no permission for My Calendar(eDiary).",
	"__invalid": {}
	```

	`[required_field_name]` not supplied
	```javascript
	__invalid: {
		"[required_field_name]": "field is required"
	}
	```

	`tchcode` does not exist
	```javascript
	__invalid: {
		"tchcode": "[tchcode] does not exist."
	}
	```

	`tchcode` is not a current teacher
	```javascript
	__invalid: {
		"tchcode": "[tchcode] has been terminated."
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
			"tchcode":"AJ",
			"start_date":"2018-05-01",
			"end_date":"2019-05-01",
			"feedcode":"per,sch,tt,act,tour,pti"
		}
	```

* **Sample GET:** (With URL Encoded `token`)

	```HTML
	http://api.tasscloud.com.au/tassweb/api/?method=getTeacherEDiary&appcode=API19&company=10&v=2&token=PQty00DXnXem4ZMp428A%2FwD6a5TB7HUYMta3sKtv89XwPsa%2FeB2RtUrAA5%2FWSxTA%2F%2Bm30VOCYMahvOVWTkTOmFJKzT8N67mvjRyULtu51I4%3D
	```
	
* **Sample POST:**

	```HTML
	<form id="postForm" name="postForm" method="POST" action="http://api.tasscloud.com.au/tassweb/api/">
		 <input type="hidden" name="method" value="getTeacherEDiary">
		 <input type="hidden" name="appcode" value="API19">
		 <input type="hidden" name="company" value="10">
		 <input type="hidden" name="v" value="2">
		 <textarea name="token">PQty00DXnXem4ZMp428A/wD6a5TB7HUYMta3sKtv89XwPsa/eB2RtUrAA5/WSxTA/+m30VOCYMahvOVWTkTOmFJKzT8N67mvjRyULtu51I4=</textarea>
	</form>
	```
