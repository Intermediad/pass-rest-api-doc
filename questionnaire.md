| URI                                                                  | Method | Returns                                     |
| -------------------------------------------------------------------- | ------ | ------------------------------              |
| [/questionnaire/v1/surveydefinition](#retrieve-surveydefinitions)    | `GET`  | retrieve all surveydefinitions              |
| [/questionnaire/v1/surveydefinition/:id](#retrieve-surveydefinition) | `GET`  | retrieve one surveydefinition               |
| [/questionnaire/v1/questionnaire/:id](#retrieve-questionnaire)       | `GET`  | retrieve a questionnaire                    |
| [/questionnaire/v1/survey](#submit-survey)                           | `POST` | Submit a completed survey                   |
| [/questionnaire/v1/surveyfile](#submit-surveyfile)                   | `POST` | Upload a file for a question of type 'File' |

## **Retrieve surveydefinitions**

Retrieve all surveydefinitions that are valid on the date of request for a specific card organization.
Card organizaton is determined by the bearer token used for authorization.

- **URL**

  /questionnaire/v1/surveydefinition

- **Method:**

  `GET`

- **Headers**

  **Required:**

  `Authorization` (type: Bearer)

- **URL Params**

  None
  
- **Data Params**

  None

- **Success Response:**

  - **Code:** 200 <br />
    **Message:** OK <br />
    **Content:** <br />

    ```javascript
		{
		"number_of_items": 2,
		"SurveyDefinitions": [
			{
			"Surveydefinition_id": 11131111177581,
			"Surveydefinition_name": "Meedoenregeling Wijk bij duurstede",
			"Description": "Vragenlijst t.b.v. het aanvragen van de meedoen regeling ",
			"Validfrom_date": "01-01-2024",
			"Validuntil_date": "30-11-2024",
			"Surveyobject_type": "Regeling",
			"Surveyobject_id": 88388383,
			"Surveyobject_code": "MD2024",
			"Surveyobject_name": "Meedoen regeling",
			"SurveySteps": [
				{
				"Step_id": 3834988,
				"Step_number": 1,
				"Step_name": "Persoonlijke situatie",
				"Description": "Vragen t.b.v. bepaling recht op meedoen",
				"Questionnaire_id": 45366636663
				},
        {
				"Step_id": 3834989,
				"Step_number": 2,
				"Step_name": "Upload documenten",
				"Description": "Upload relevante documenten bij uw aanvraag van de meedoen regeling",
				"Questionnaire_id": 45366636664
				}
			]
			},
			{
			"Surveydefinition_id": 111111111111112,
			"Surveydefinition_name": "Witgoedregeling Wijk bij duurstede",
			"Description": "Vragenlijst t.b.v. het aanvragen van de witgoed regeling ",
			"Validfrom_date": "01-06-2024",
			"Validuntil_date": "31-08-2024",
			"Surveyobject_type": "Regeling",
			"Surveyobject_id": 88388384,
			"Surveyobject_code": "WG2024",
			"Surveyobject_name": "Witgoed regeling",
			"SurveySteps": [
				{
				"Step_id": 3834990,
				"Step_number": 1,
				"Step_name": "Persoonlijke situatie"
				"Description": "Vragen t.b.v. bepaling recht op de regelung",
				"Questionnaire_id": 45366636665
				},
        {
				"Step_id": 3834991,
				"Step_number": 2,
				"Step_name": "Upload documenten",
				"Description": "Upload relevante documenten bij uw aanvraag van de witgoedregeling",
				"Questionnaire_id": 45366636666
				}
			]
			}
		]
		}
    ```

  - **Code:** 204 <br />
    **Message:** No data found <br />

- **Content definition:**

| Name                                      | Type         | Optional | Additional information |
| :---------------------------------------- | :----------- | :------- | :--------------------- |
| _`Root`_                                  | object       |          | 
| &nbsp;&nbsp;`number_of_items`             | Integer      |          | 0, 1 or more
| _`Surveydefinitions`_                     | object       |          | 
| &nbsp;&nbsp;`Surveydefinition_id`         | long         |          | Unique identifier
| &nbsp;&nbsp;`Surveydefinition_name`       | string(100)  |          | 
| &nbsp;&nbsp;`Description`                 | string(2000) | Yes      | 
| &nbsp;&nbsp;`Validfrom_date`              | string(10)   |          | format 'dd-MM-yyyy'
| &nbsp;&nbsp;`Validuntil_date`             | string(10)   |          | format 'dd-MM-yyyy'
| &nbsp;&nbsp;`Surveyobject_type`           | enum         |          | Values: Regeling, Voorziening 
| &nbsp;&nbsp;`Surveyobject_id`             | long         |          | Unique identifier of surveyobject
| &nbsp;&nbsp;`Surveyobject_code`           | string(50)   |          | Unique code of surveyobject
| &nbsp;&nbsp;`Surveyobject_name`           | string(200)  |          | Name of surveyobject
| _`SurveySteps`_                           | object       |          | 1 or more
| &nbsp;&nbsp;`Step_id`                     | long         |          | Unique identifier
| &nbsp;&nbsp;`Step_number`                 | Integer      |          | 
| &nbsp;&nbsp;`Step_name`                   | string(100)  |          | 
| &nbsp;&nbsp;`Description`                 | string(2000) | Yes      | 
| &nbsp;&nbsp;`Questionnaire_id`            | long         |          | Unique identification of the questionnaire to be used in the survey step

- **Error Response:**

  - **Code:** 406 <br />
      **Message:** Authorization header missing
  - **Code:** 406 <br />
      **Message:** Auth bearer unknown
  - **Code:** 401 <br />
      **Message:** Authorization header invalid
  - **Code:** 401 <br />
      **Message:** Token invalid or not found
  - **Code:** 401 <br />
      **Message:** Token expired
  - **Code:** 401 <br />
      **Message:** API key not authorized

<br />

## **Retrieve surveydefinition**

Retrieve one surveydefinitions by id that is valid on the date of request for a specific card organization.
Card organizaton is determined by the bearer token used for authorization.

- **URL**

  /questionnaire/v1/surveydefinition

- **Method:**

  `GET`

- **Headers**

  **Required:**

  `Authorization` (type: Bearer)

- **URL Params**

  **Required:**

  `:surveydefinition_id`
  
- **Data Params**

  None

- **Success Response:**

  - **Code:** 200 <br />
    **Message:** OK <br />
    **Content:** <br />

    ```javascript
		{
		"number_of_items": 1,
		"SurveyDefinitions": [
			{
			"Surveydefinition_id": 11131111177581,
			"Surveydefinition_name": "Meedoenregeling Wijk bij duurstede",
			"Description": "Vragenlijst t.b.v. het aanvragen van de meedoen regeling ",
			"Validfrom_date": "01-01-2024",
			"Validuntil_date": "30-11-2024",
			"Surveyobject_type": "Regeling",
			"Surveyobject_id": 88388383,
			"Surveyobject_code": "MD2024",
			"Surveyobject_name": "Meedoen regeling",
			"SurveySteps": [
				{
				"Step_id": 3834988,
				"Step_number": 1,
				"Step_name": "Persoonlijke situatie",
				"Description": "Vragen t.b.v. bepaling recht op meedoen",
				"Questionnaire_id": 45366636663
				},
        {
				"Step_id": 3834989,
				"Step_number": 2,
				"Step_name": "Upload documenten",
				"Description": "Upload relevante documenten bij uw aanvraag van de meedoen regeling",
				"Questionnaire_id": 45366636664
				}
			]
			}
		]
		}
    ```

  - **Code:** 204 <br />
    **Message:** No data found <br />

- **Content definition:**

| Name                                      | Type         | Optional | Additional information |
| :---------------------------------------- | :----------- | :------- | :--------------------- |
| _`Root`_                                  | object       |          | 
| &nbsp;&nbsp;`number_of_items`             | Integer      |          | 0 or 1
| _`Surveydefinitions`_                     | object       |          | 
| &nbsp;&nbsp;`Surveydefinition_id`         | long         |          | Unique identifier
| &nbsp;&nbsp;`Surveydefinition_name`       | string(100)  |          | 
| &nbsp;&nbsp;`Description`                 | string(2000) | Yes      | 
| &nbsp;&nbsp;`Validfrom_date`              | string(10)   |          | format 'dd-MM-yyyy'
| &nbsp;&nbsp;`Validuntil_date`             | string(10)   |          | format 'dd-MM-yyyy'
| &nbsp;&nbsp;`Surveyobject_type`           | enum         |          | Values: Regeling, Voorziening 
| &nbsp;&nbsp;`Surveyobject_id`             | long         |          | Unique identifier of surveyobject
| &nbsp;&nbsp;`Surveyobject_code`           | string(50)   |          | Unique code of surveyobject
| &nbsp;&nbsp;`Surveyobject_name`           | string(200)  |          | Name of surveyobject
| _`SurveySteps`_                           | object       |          | 1 or more
| &nbsp;&nbsp;`Step_id`                     | long         |          | Unique identifier
| &nbsp;&nbsp;`Step_number`                 | Integer      |          | 
| &nbsp;&nbsp;`Step_name`                   | string(100)  |          | 
| &nbsp;&nbsp;`Description`                 | string(2000) | Yes      | 
| &nbsp;&nbsp;`Questionnaire_id`            | long         |          | Unique identification of the questionnaire to be used in the survey step

- **Error Response:**

  - **Code:** 406 <br />
      **Message:** Authorization header missing
  - **Code:** 406 <br />
      **Message:** Auth bearer unknown
  - **Code:** 401 <br />
      **Message:** Authorization header invalid
  - **Code:** 401 <br />
      **Message:** Token invalid or not found
  - **Code:** 401 <br />
      **Message:** Token expired
  - **Code:** 401 <br />
      **Message:** API key not authorized

<br />

## **Retrieve questionnaire**

Retrieve one active questionnaire by id for a specific card organization.
Card organizaton is determined by the bearer token used for authorization.

- **URL**

  /questionnaire/v1/questionnaire

- **Method:**

  `GET`

- **Headers**

  **Required:**

  `Authorization` (type: Bearer)

- **URL Params**

  **Required:**

  `:questionnaire_id`
  
- **Data Params**

  None

- **Success Response:**

  - **Code:** 200 <br />
    **Message:** OK <br />
    **Content:** <br />

    ```javascript
		{
		"Questionnaire_id": 111111111111111,
		"Questionnaire_name": " Naam van de Questionnaire",
		"Description": "Omschrijving van de questionnaire",
		"Questions": [
			{
			"Question_id": 111111111111111,
			"Question": "Burgelijke staat?",
			"Answer_type": "Enum",
			"Sort_order": 1,
			"LovDefinition": {
				"Lov_id": 111111111111111,
				"Name": "Naam van de keuzelijst",
				"Description": "Omschrijving van de inhoud van de keuzelijst",
				"Is_boolean": false,
				"LovValues": [
				{
					"Value_id": 111111111111111,
					"Sort_order": 1,
					"Value_key": "K1",
					"Value_caption": "Keuze 1",
					"Explanation": "Uitleg bij de keuzewaarde"
				},
				{
					"Value_id": 111111111111112,
					"Sort_order": 2,
					"Value_key": "K2",
					"Value_caption": "Keuze 2",
					"Explanation": "Uitleg bij de keuzewaarde"
				} ]
			},
			"AnswerConstraints": [
				{
				"Constraint_id": 111111111111111,
				"Constraint_type": "Type_enum",
				"Error_message": "Errortekst bij constraint1",
				"Constraint_value_Date": "21-08-2020",
				"Constraint_value_Int": 4214,
				"Constraint_value_Dec": 44.22,
				"Constraint_value_Regex": "#@/Aa-Zz00/",
				"Constraint_valuekey_Lov": "A",
				"Currentdate_default": false
				} ],
			"FollowupConstraints": [
				{
				"Constraint_id": 111111111111111,
				"Constraint_type": "Enum",
				"Constraint_value_Date": "21-08-2020",
				"Constraint_value_Int": 4214,
				"Constraint_value_Dec": 44.22,
				"Constraint_value_Regex": "#@/Aa-Zz00/",
				"Questionnare_id": 111111111111111,
				"Constraint_LovValues": [
					{
					"Value_key": "A"
					} ]
				} ]
			} ]
		}
    ```

  - **Code:** 204 <br />
    **Message:** No data found <br />

- **Content definition:**

| Name                                      | Type         | Optional | Additional information |
| :---------------------------------------- | :----------- | :------- | :--------------------- |
| _`Root`_                                  | object       |          | 1 questionnaire object
| &nbsp;&nbsp;`Questionnaire_id`            | long         |          | Unique identifier
| &nbsp;&nbsp;`Questionnaire_name`          | string(100)  |          | 
| &nbsp;&nbsp;`Description`                 | string(2000) | Yes      | 
| _`Questions`_                             | object       |          | 1 or more questions
| &nbsp;&nbsp;`Question_id`                 | long         |          | Unique identifier
| &nbsp;&nbsp;`Question`                    | string(200)  |          | 
| &nbsp;&nbsp;`Answer_type`                 | enum         |          | Values: Open, Lov, Date, _Int, Dec, File
| &nbsp;&nbsp;`Sort_order`                  | integer      |          | 
| &nbsp;&nbsp;`Description`                 | string(2000) | Yes      |  
| _`LovDefinition`_                         | object       |          | 0, 1; Only when Answertype = 'Lov'
| &nbsp;&nbsp;`Lov_id`                      | long         |          | Unique identifier
| &nbsp;&nbsp;`Name`                        | string(200)  |          | 
| &nbsp;&nbsp;`Description`                 | enum         | Yes      | Values: Open, Lov, Date, _Int, Dec, File
| &nbsp;&nbsp;`Is_boolean`                  | boolean      |          | Indicates if Lov represent a boolean value. Values: true or false
| _`LovValue`_                              | object       |          | 1 or more; detail of LovDefinition
| &nbsp;&nbsp;`Value_id`                    | long         |          | Unique identifier
| &nbsp;&nbsp;`Sort_order`                  | integer      |          | 
| &nbsp;&nbsp;`Value_key`                   | string(50)   |          | Unique Key value within Lovdefinition
| &nbsp;&nbsp;`Value_caption`               | string(50)   |          | Value as shown to the respondent
| &nbsp;&nbsp;`Explanation`                 | string(1000) | Yes      | 
| _`AnswerConstraints`_                     | object       |          | Cosntraints for validating the answer to a question; 0, 1 or more; detail of Question
| &nbsp;&nbsp;`Constraint_id`               | long         |          | Unique identifier
| &nbsp;&nbsp;`Constraint_type`             | enum         |          | Values: Mandatory, Greater, Smaller, GreaterEqual, SmallerEqual, StringLength, Regex, DefaultValue, HasRemark
| &nbsp;&nbsp;`Error_message`               | string(200)  |          | Message shown to respondent when constraint is violated
| &nbsp;&nbsp;`Constraint_value_Date`       | string(10)   | Yes      | Only when Answer_type = 'Date' and Constraint_type in; Greater, Smaller, GreaterEqual, SmallerEqual, DefaultValue . Format 'dd-MM-yyyy'
| &nbsp;&nbsp;`Constraint_value_Int`        | integer      | Yes      | Only when Answer_type = '_Int' and Constraint_type in; Greater, Smaller, GreaterEqual, SmallerEqual, DefaultValue
| &nbsp;&nbsp;`Constraint_value_Dec`        | decimal      | Yes      | Only when Answer_type = 'Dec'  and Constraint_type in; Greater, Smaller, GreaterEqual, SmallerEqual, DefaultValue
| &nbsp;&nbsp;`Constraint_value_Regex`      | string(200)  | Yes      | Only when Answer_type = 'Open' and Constraint_type in; Regex, DefaultValue
| &nbsp;&nbsp;`Constraint_valuekey_Lov`     | string(50)   | Yes      | Only when Answer_type = 'Lov'  and Constraint_type in; DefaultValue
| &nbsp;&nbsp;`Currentdate_default`         | integer      | Yes      | Only when Answer_type = 'Date' and Constraint_type in; DefaultValue 
| _`FollowupConstraints`_                   | object       |          | Contraints that specify the condition voor a subquestionnaire; 0, 1 or more; detail of Question
| &nbsp;&nbsp;`Constraint_id`               | long         |          | Unique identifier
| &nbsp;&nbsp;`Constraint_type`             | enum         |          | Values: Greater, Smaller, GreaterEqual, SmallerEqual, StringLength, LovValue, Regex
| &nbsp;&nbsp;`Error_message`               | string(200)  |          | Message shown to respondent when constraint is violated
| &nbsp;&nbsp;`Constraint_value_Date`       | string(10)   | Yes      | Only when Answer_type = 'Date' and Constraint_type in; Greater, Smaller, GreaterEqual, SmallerEqual . Format 'dd-MM-yyyy'
| &nbsp;&nbsp;`Constraint_value_Int`        | integer      | Yes      | Only when Answer_type = '_Int' and Constraint_type in; Greater, Smaller, GreaterEqual, SmallerEqual
| &nbsp;&nbsp;`Constraint_value_Dec`        | decimal      | Yes      | Only when Answer_type = 'Dec'  and Constraint_type in; Greater, Smaller, GreaterEqual, SmallerEqual
| &nbsp;&nbsp;`Constraint_value_Regex`      | string(200)  | Yes      | Only when Answer_type = 'Open' and Constraint_type in; Regex
| &nbsp;&nbsp;`Questionnare_id`             | long         | Yes      | Unique id of (sub)questionnaire that should be activated
| _`Constraint_LovValues`_                  | object       | Yes      | Only when Answer_type = 'Lov' and Constraint_type in; LovValue;  1 or more
| &nbsp;&nbsp;`Value_key`                   | string(50)   |          | ValueKey of the Lovvalue

- **Error Response:**

  - **Code:** 406 <br />
      **Message:** Authorization header missing
  - **Code:** 406 <br />
      **Message:** Auth bearer unknown
  - **Code:** 401 <br />
      **Message:** Authorization header invalid
  - **Code:** 401 <br />
      **Message:** Token invalid or not found
  - **Code:** 401 <br />
      **Message:** Token expired
  - **Code:** 401 <br />
      **Message:** API key not authorized
  - **Code:** 400 <br />
      **Message:** Missing "Questionnaire_id" parameter

<br />

## **Submit survey**

Submit a completed survey. 

- **URL**

  /questionnaire/v1/survey

- **Method:**

  `POST`

- **Headers**

  **Required:**

  `Authorization` (type: Bearer)

- **URL Params**

  None
  
- **Data Params**
  
  Request-Body /JSON/:
  
    ```javascript
		{
			"SurveyDefinition_id": 111111111111111,
			"Respondent":
			{
				"Identification_type": "GAN",
				"Identification": 111111111111,
				"First_name": "Kees",
				"Initials": "C.L.",
				"Infix": "van",
				"Last_name": "Kooten",
				"Gender": "M",
				"Email_adress": "mail@mailbox.nl",
				"Phone_number": "0648978933"
			},
			"Answer": [
			{
				"Answer_id": 111111111111111,
				"Question_id": 111111111111111,
				"Answer_integer": 2,
				"Answer_string": "Dit is het antwoord",
				"Answer_date": "23-09-2024",
				"Answer_decimal": 12.22,
				"Answer_valuekey_lov": "A",   
				"Remark": "Dit is een opmerking",
			} ]
		}
    ```

- **Content definition:**

| Name                                      | Type         | Optional | Additional information |
| :---------------------------------------- | :----------- | :------- | :--------------------- |
| _`Root`_                                  | object       |          | 1 questionnaire object
| &nbsp;&nbsp;`SurveyDefinition_id`         | Long         |          | 
| _`Answers`_                               | object       |          | 1 or more answers
| &nbsp;&nbsp;`Answer_integer`              | integer      | Yes      | only if the answer concerns an integer value
| &nbsp;&nbsp;`Answer_string`               | string(1000) | Yes      | only if the answer concerns a string value
| &nbsp;&nbsp;`Answer_date`                 | string       | Yes      | only if the answer concerns a date value; format 'dd-MM-yyyy'
| &nbsp;&nbsp;`Answer_decimal`              | decimal      | Yes      | only if the answer concerns a decimal value
| &nbsp;&nbsp;`Answer_valuekey_lov`         | long         | Yes      | only if the answer concerns a lov value
| &nbsp;&nbsp;`Remark`                      | string(1000) | Yes      | 
| &nbsp;&nbsp;`Question_id`                 | long         |          | unique id of the question
| _`Respondent`_                            | object       |          | the person who fills out the survey
| &nbsp;&nbsp;`Identification_type`         | enum         | Yes      | values: BSN, GAN, ...
| &nbsp;&nbsp;`Identification`              | long         | Yes      | identificationnr for chosen type
| &nbsp;&nbsp;`First_name`                  | string(20)   | Yes      | 
| &nbsp;&nbsp;`Initials`                    | string(20)   |          | 
| &nbsp;&nbsp;`Infix`                       | string(20)   | Yes      | 
| &nbsp;&nbsp;`Last_name`                   | string(50)   |          | 
| &nbsp;&nbsp;`Gender`                      | enum         |          | values: M(ale), F(emale), O(ther)
| &nbsp;&nbsp;`Email_adress`                | string(100)  |          | 
| &nbsp;&nbsp;`Phone_number`                | string(20)   | Yes      | 

- **Success Response:**

  - **Code:** 200 <br />
    **Message:** OK <br />

- **Output Params**

  `:survey_id`

- **Error Response:**

  - **Code:** 406 <br />
      **Message:** Authorization header missing
  - **Code:** 406 <br />
      **Message:** Auth bearer unknown
  - **Code:** 401 <br />
      **Message:** Authorization header invalid
  - **Code:** 401 <br />
      **Message:** Token invalid or not found
  - **Code:** 401 <br />
      **Message:** Token expired
  - **Code:** 401 <br />
      **Message:** API key not authorized
  - **Code:** 400 <br />
      **Message:** Missing "Questionnaire_id" parameter

<br />

## **Submit surveyfile**

Submit a completed survey. 

- **URL**

  /questionnaire/v1/surveyfile

- **Method:**

  `POST`

- **Headers**

  **Required:**

  `Authorization` (type: Bearer)
  `Content_Type` 

- **URL Params**

  **Required:**

  `:survey_id` (survey_id returned by the POST survey rest call)
  `:question_id` (id of question the file is attached to)
  
- **Data Params**
  
  Binary object (filedocument)
  
- **Success Response:**

  - **Code:** 200 <br />
    **Message:** Binary content succesfully received for {survey_id} / {question_id} <br />

- **Error Response:**

  - **Code:** 406 <br />
      **Message:** Authorization header missing
  - **Code:** 406 <br />
      **Message:** Auth bearer unknown
  - **Code:** 401 <br />
      **Message:** Authorization header invalid
  - **Code:** 401 <br />
      **Message:** Token invalid or not found
  - **Code:** 401 <br />
      **Message:** Token expired
  - **Code:** 401 <br />
      **Message:** API key not authorized
  - **Code:** 400 <br />
      **Message:** 'Content-Type header missing'
  - **Code:** 400 <br />
      **Message:** 'Content-Type {value} not allowed for document'
  - **Code:** 400 <br />
      **Message:** ''No binary content received''
  - **Code:** 400 <br />
      **Message:** 'Path parameter {survey_id} empty or missing'
  - **Code:** 400 <br />
      **Message:** 'Path parameter {question_id} empty or missing'
  - **Code:** 406 <br />
      **Message:** 'Survey for {survey_id} not found'
  - **Code:** 406 <br />
      **Message:** 'Survey for {survey_id} has invalid status and cannot be changed'
  - **Code:** 406 <br />
      **Message:** 'Answer for {survey_id} / {question_id} not found'
  - **Code:** 406 <br />
      **Message:** 'File for {survey_id} / {question_id} already present'
  - **Code:** 422 <br />
      **Message:** 'An error occurred while processing filedocument for {survey_id} / {question_id}'