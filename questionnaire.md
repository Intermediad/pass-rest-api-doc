| URI                                                                  | Method | Returns                        |
| -------------------------------------------------------------------- | ------ | ------------------------------ |
| [/questionnaire/v1/surveydefinition](#retrieve-surveydefinitions)    | `GET`  | retrieve all surveydefinitions |
| [/questionnaire/v1/surveydefinition/:id](#retrieve-surveydefinition) | `GET`  | retrieve one surveydefinition  |
| [/questionnaire/v1/questionnaire/:id](#retrieve-questionnaire)       | `GET`  | retrieve a questionnaire       |

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