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
				"location": "",
				"attachment": {
					"deep_link": "",
					"file_name": ""
				},
				"url_text": "",
				"day_time_desc": "Fri 21 Oct 2016 at 12:00am (End 12:00am)",
				"campus_code": "",
				"dayFlag": "",
				"summary": "a great big event",
				"has_attachment": false,
				"description": "a great big event",
				"single_day": true,
				"year_groups": {},
				"source": "school",
				"title": "Brad's event",
				"start": "2016-10-21 00:00:00",
				"end": "2016-10-21 00:00:00",
				"id": 7340,
				"url_link": "",
				"feed": "School and Teacher Calendar",
				"all_day": true
			},
			{
				"location": "",
				"attachment": {},
				"url_text": "",
				"day_time_desc": "",
				"summary": "Mr A Johnstone in ",
				"description": "Lesson 4: English PK.A with Mr A Johnstone",
				"has_attachment": false,
				"single_day": true,
				"source": "timetable",
				"start": "2019-01-31 11:30:00",
				"end": "2019-01-31 12:29:00",
				"title": "English",
				"id": "timetable_86_0001_4_4_-1|A_class",
				"url_link": "",
				"all_day": false,
				"feed": "My Timetable"
			},
			{
				"location": "",
				"attachment": {},
				"deep_link": "{\"target\":\"curricular.activity\",\"empcode\":\"1000016\",\"activity_assign_id\":\"3814\",\"prod_menu\":\"N\"}",
				"url_text": "Go To This Activity",
				"day_time_desc": "",
				"summary": "Ancient History 11 A\nActivity Available From: Mon 18 Apr 2016 at 05:19 PM",
				"description": "Ancient History 11 A\nActivity Available From: Mon 18 Apr 2016 at 05:19 PM",
				"has_attachment": false,
				"single_day": true,
				"source": "activity",
				"start": "2016-04-18 17:19:00",
				"end": "",
				"title": " Ancient History 11 A - Activity Available",
				"id": 3814,
				"url_link": "",
				"all_day": false,
				"feed": "LMS / Assessment Activities"
			},
			{
				"location": "Art Room",
				"attachment": {},
				"allDay": false,
				"url_text": "Go To This Student",
				"end_date": "2018-12-25",
				"start_date": "2018-12-25",
				"day_time_desc": "",
				"summary": "PT Interview\n11 11/12 Accounting",
				"description": "PT Interview\nAndy Clark\n11 11/12 Accounting",
				"has_attachment": false,
				"source": "pti",
				"title": "11/12 Accounting - Andy Clark",
				"id": 100162,
				"url_link": "tiamenu/TIAFrameset3.cfm?menuUrl=tiamenu/TIAStudMenu%2Ecfm%3FstudentCode%3D0009130&menuInfoUrl=students%2FTIAStudGenDetails%2Ecfm%3FstudentCode%3D0009130",
				"feed": "Parent Teacher Interviews"
			}
		]
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
