**getEDiaryFeeds**
----
	Returns a list of eDiary feeds as per the program Kiosk Calendar > Calendar Feeds (Setup).
	
* **Version History:**

	TASS v51.2 - Method Added

* **Version:**

	2

* **Method:**

	`GET | POST`
	
*  **Params:**

	**Required:**

	`type [string]` - Must be one of "T" or "S".

	**Optional:**

	`codeonly [bool]` - Defaults to `false`

	**Conditional:**
	
	none

* **Success Response:**

	```javascript
		{
			"calendar": [
						{
							"code": "tt",
							"desc": "My Timetable"
						},
						{
							"code": "act",
							"desc": "LMS / Assessment Activities"
						},
						{
							"code": "pti",
							"desc": "Parent Teacher Interviews"
						}
			],
			"__tassversion": "01.053.3.000",
			"token": {
					"timestamp": "{ts '2021-01-25 10:09:28'}",
					"codeonly": false,
					"type": "T"
			}
		}
	```
 
* **Error Response:**

	`type` not supplied
	```javascript
	"__invalid": {
		"type": "field is required"
	}
	```

	`type` must be "T" or "S"
	```javascript
	"__invalid": {
		"type": "Type must be one of 'T' and 'S'."
	}
	```

	`codeonly` must be 'true' or 'false'
	```javascript
	"__invalid": {
		"codeonly": "Value is not a valid boolean."
	}
	```

* **Sample Parameters:**

	```javascript
		{
			"type":"T",
			"codeonly":"false"
		}
	```

* **Sample GET:** (With URL Encoded `token`)

	```HTML
	http://api.tasscloud.com.au/tassweb/api/?method=getEDiaryFeeds&appcode=API19&company=10&v=2&token=PQty00DXnXem4ZMp428A%2FwD6a5TB7HUYMta3sKtv89XwPsa%2FeB2RtUrAA5%2FWSxTA%2F%2Bm30VOCYMahvOVWTkTOmFJKzT8N67mvjRyULtu51I4%3D
	```
	
* **Sample POST:**

	```HTML
	<form id="postForm" name="postForm" method="POST" action="http://api.tasscloud.com.au/tassweb/api/">
		 <input type="hidden" name="method" value="getEDiaryFeeds">
		 <input type="hidden" name="appcode" value="API19">
		 <input type="hidden" name="company" value="10">
		 <input type="hidden" name="v" value="2">
		 <textarea name="token">PQty00DXnXem4ZMp428A/wD6a5TB7HUYMta3sKtv89XwPsa/eB2RtUrAA5/WSxTA/+m30VOCYMahvOVWTkTOmFJKzT8N67mvjRyULtu51I4=</textarea>
	</form>
	```
