# AmazingHiring API v6

AmazingHiring API is a set of endpoints for integration of AmazingHiring with your product.

Current version: 6.

Base API url: **https://search.amazinghiring.com/api/v6/**

## Authorization

All API endpoints require an access token.

Remember to keep your token secret, treat it just like password! It acts on behalf of your company and has access to private data when interacting with the API.

### Access token generation
The token can be created through the web UI on user settings page,
which is **available after approval** from [AmazingHiring sales manager](mailto:sales@amazinghiring.com).

### Use the access token

The token key should be included in the `Authorization` header.
The key should be prefixed by the string literal "Token" \(or "Bearer" if your appliccatoin authorized via [oAuth2.0](https://amazinghiring.github.io/oauth2-docs/)\), with whitespace separating the two strings. For example:

```
   Authorization: Token a0b1c2d3e4f5
```

## Pagination

### How do I know if there are more pages?

If there are more pages, the response will be provided with `Link` header. Example:

```
Link: <https://search.amazinghiring.com/api/v6/candidates/?page=2; rel="next">, <https://search.amazinghiring.com/api/v6/candidates/?page=7; rel="last">
```

To get `N` page you have to pass page number via GET-parameter. Example:

```
https://search.amazinghiring.com/api/v6/candidates/?page=2
```

## Profiles

* [**GET**	`/profiles/{profile_id}/` Returns profile by id](#get-profile-by-id)

### GET Profile by id

Request example:

```
curl -H "Authorization: Token ${TOKEN}" -H "Accept: application/json" "https://search.amazinghiring.com/api/v6/profiles/${PROFILE_ID}/"
```

Response example:

```json
{
  "id": 1,
  "name": "Иван I",
  "avatars": [
    "https://avatars0.githubusercontent.com/u/ivanI",
    "https://avatars1.githubusercontent.com/u/ivanI"
  ],
  "age": 30,
  "birthday": "1990-01-01",
  "comments": [
    {
      "id": 1,
      "body": "Тело комментария",
      "user": {
        "id": 1,
        "name": "Иван II Рекрутеров"
      },
      "created_at": "2015-09-10T05:59:57.660Z",
      "modified_at": null
    }
  ],
  "resumes": [
    {
      "id": 2,
      "type": "hh",
      "url": "",
      "created_at": "2015-09-10T05:59:57.660Z",
      "user": {
        "id": 1,
        "name": "Иван II Рекрутеров"
      }
    }
  ],
  "links": [
    {
      "value": "https://github.com/ivanI",
      "personal_site": false,
      "source": {
        "type": "public",
        "url": "https://github.com/ivan",
        "created_at": "2015-09-10T05:59:57.660Z"
      }
    },
    {
      "value": "https://ivani.ru",
      "personal_site": true,
      "source": {
        "type": "public",
        "url": "https://ivani.ru",
        "created_at": "2015-09-10T05:59:57.660Z"
      }
    },
    {
      "value": "https://vk.com/ivan",
      "personal_site": false,
      "source": {
        "id": 1,
        "type": "manual",
        "created_at": "2015-09-10T05:59:57.660Z",
        "url": "",
        "user": {
          "id": 1,
          "name": "Иван II Рекрутеров"
        }
      }
    }
  ],
  "contacts": [
    {
      "value": "+7 (999) 123 12 12",
      "type": "phone",
      "source": {
        "id": 4,
        "type": "resume-hh",
        "url": "",
        "created_at": "2015-09-10T10:23:57.660Z",
        "user": {
          "id": 1,
          "name": "Иван II Рекрутеров"
        }
      }
    },
    {
      "value": "ivanI",
      "type": "skype",
      "source": {
        "type": "public",
        "url": "https://api.github.com/users/ivanI",
        "created_at": "2015-09-10T10:23:57.660Z"
      }
    }
  ],
  "locations": [
    {
      "id": "Moscow, MO, Russia",
      "name": "Москва, Россия"
    }
  ],
  "educations": [
    {
      "start": "2008-09",
      "end": "2014-06",
      "name": "МГТУ им. Н.Э. Баумана",
      "faculty": "Информатика и системы управления",
      "specialization": "ИУ5 Системы обработки информации и управления",
      "degree": "Магистр"
    }
  ],
  "positions": [
    {
      "start": "2012-01",
      "end": "2014-03",
      "company": {
        "id": "Ivan Corp",
        "name": "Ivan Corp.",
        "site": "http://ivancorp.ru/"
      },
      "position": "Начальник начальников",
      "description": "Делал самую главную работу"
    }
  ],
  "courses_or_certificates": [
    {
      "name": "Classic English Course",
      "organization_name": "Course",
      "start": "2012-01",
      "end": "2012-02"
    }
  ],
  "test_results": [
    {
      "id": 1,
      "right_answers": 32,
      "exam_start": "2015-09-10T10:23:57.660Z",
      "exam_stop": "2015-09-10T11:05:43.430Z",
      "view_url": "https://certification.mail.ru/tests/result/ivanI/",
      "invite": {
        "id": "1cafa7f85ebe11e5a39a0cc47a001060",
        "short_link": "http://bit.ly/1",
        "created_at": "2015-09-09T11:05:43.430Z",
        "user": {
          "id": 1,
          "name": "Иван II Рекрутеров"
        }
      },
      "test": {
        "id": "python",
        "name": "Python (20 мин)",
        "provider_id": 0,
        "questions_total": 45,
        "threshold": 30
      }
    }
  ],
  "skills": [
    {
      "name": "python",
      "rating": 4.95,
      "sources": [
        {
          "type": "public",
          "url": "http://ua.linkedin.com/pub/ivanI",
          "created_at": "2015-09-10T05:59:57.660Z"
        }
      ],
      "additional_skills": [
        {
          "name": "django",
          "rating": 4.1,
          "sources": [
            {
              "type": "public",
              "url": "http://ua.linkedin.com/pub/ivanI",
              "created_at": "2015-09-10T05:59:57.660Z"
            },
            {
              "id": 4,
              "type": "resume-hh",
              "url": "",
              "created_at": "2015-09-10T10:23:57.660Z",
              "user": {
                "id": 1,
                "name": "Иван II Рекрутеров"
              }
            }
          ]
        }
      ]
    }
  ]
}
```

## Folders

* [Folder object](#folder-object)
* [**GET**	`/folders/` Returns folders list](#get-folders)
* [**GET**	`/folders/{folder_id}/` Returns folder object by id](#get-folder-by-id)
* [**POST**	`/folders/` Creates folder](#create-folder)
* [**PATCH**	`/folders/{folder_id}/` Updates folder](#update-folder)
* [**DELETE**	`/folders/{folder_id}/` Deletes folder](#delete-folder)


### Folder object

Example of folder object:

```json
{
    "assignees": [],
    "candidate_statuses": [
        {
            "id": 2,
            "name": "selected",
            "order": 0
        },
        {
            "id": 4,
            "name": "mailing_list",
            "order": 2
        },
        {
            "id": 6,
            "name": "interview",
            "order": 3
        },
        {
            "id": 8,
            "name": "offer",
            "order": 4
        },
        {
            "id": 9,
            "name": "unopened",
            "order": 0
        },
        {
            "id": 10,
            "name": "opened",
            "order": 1
        },
        {
            "id": 11,
            "name": "replied",
            "order": 2
        },
        {
            "id": 13,
            "name": "reject",
            "order": 5
        }
    ],
    "created_at": "2018-08-15T07:04:35.654679Z",
    "description": "",
    "id": 1,
    "modified_at": "2018-08-15T07:04:35.654860Z",
    "name": "Folder 1",
    "owner": {
        "email": "user@acme.com",
        "first_name": "User",
        "id": 1,
        "last_name": "User"
    },
    "status": "active"
}
```

### Get folders

**GET**	`/folders/`

Returns array of folder objects.

Request example:

```
curl -H "Authorization: Token ${TOKEN}" -H "Accept: application/json" "https://search.amazinghiring.com/api/v6/folders/"
```

Response example:

```json
[
	{
	    "assignees": ["user@acme.com"],
	    "candidate_statuses": [
	        {
	            "id": 2,
	            "name": "selected",
	            "order": 0
	        },
	        {
	            "id": 4,
	            "name": "mailing_list",
	            "order": 2
	        },
	        {
	            "id": 6,
	            "name": "interview",
	            "order": 3
	        },
	        {
	            "id": 8,
	            "name": "offer",
	            "order": 4
	        },
	        {
	            "id": 9,
	            "name": "unopened",
	            "order": 0
	        },
	        {
	            "id": 10,
	            "name": "opened",
	            "order": 1
	        },
	        {
	            "id": 11,
	            "name": "replied",
	            "order": 2
	        },
	        {
	            "id": 13,
	            "name": "reject",
	            "order": 5
	        }
	    ],
	    "created_at": "2018-08-15T07:04:35.654679Z",
	    "description": "",
	    "id": 1,
	    "modified_at": "2018-08-15T07:04:35.654860Z",
	    "name": "Folder 1",
	    "owner": {
	        "email": "user@acme.com",
	        "first_name": "User",
	        "id": 1,
	        "last_name": "User"
	    },
	    "status": "active"
	},
	{
	    "assignees": ["user@acme.com"],
	    "candidate_statuses": [
	        {
	            "id": 2,
	            "name": "selected",
	            "order": 0
	        },
	        {
	            "id": 4,
	            "name": "mailing_list",
	            "order": 2
	        },
	        {
	            "id": 6,
	            "name": "interview",
	            "order": 3
	        },
	        {
	            "id": 8,
	            "name": "offer",
	            "order": 4
	        },
	        {
	            "id": 9,
	            "name": "unopened",
	            "order": 0
	        },
	        {
	            "id": 10,
	            "name": "opened",
	            "order": 1
	        },
	        {
	            "id": 11,
	            "name": "replied",
	            "order": 2
	        },
	        {
	            "id": 13,
	            "name": "reject",
	            "order": 5
	        }
	    ],
	    "created_at": "2018-08-15T07:04:35.654679Z",
	    "description": "",
	    "id": 2,
	    "modified_at": "2018-08-15T07:04:35.654860Z",
	    "name": "Folder 1",
	    "owner": {
	        "email": "user@acme.com",
	        "first_name": "User",
	        "id": 1,
	        "last_name": "User"
	    },
	    "status": "active"
	}
]
```

### Get folder by id

**GET**	`/folders/{folder_id}/`

Returns folder objects by id.

Request example:

```
curl -H "Authorization: Token ${TOKEN}" -H "Accept: application/json" "https://search.amazinghiring.com/api/v6/folders/1/"
```

Response example:

```json
{
    "assignees": ["user@acme.com"],
    "candidate_statuses": [
        {
            "id": 2,
            "name": "selected",
            "order": 0
        },
        {
            "id": 4,
            "name": "mailing_list",
            "order": 2
        },
        {
            "id": 6,
            "name": "interview",
            "order": 3
        },
        {
            "id": 8,
            "name": "offer",
            "order": 4
        },
        {
            "id": 9,
            "name": "unopened",
            "order": 0
        },
        {
            "id": 10,
            "name": "opened",
            "order": 1
        },
        {
            "id": 11,
            "name": "replied",
            "order": 2
        },
        {
            "id": 13,
            "name": "reject",
            "order": 5
        }
    ],
    "created_at": "2018-08-15T07:04:35.654679Z",
    "description": "",
    "id": 1,
    "modified_at": "2018-08-15T07:04:35.654860Z",
    "name": "Folder 1",
    "owner": {
        "email": "user@acme.com",
        "first_name": "User",
        "id": 1,
        "last_name": "User"
    },
    "status": "active"
}
```

### Create folder

**POST**	`/folders/`

Creates new folder.

Request body is json object with 2 parameters: `name` and `assignees`.

`name` - folder name. **Required**.

`assignees` - array of user emails. **Required**. Can be empty.

```json
{
    "assignees": [
        "user@acme.com"
    ],
    "name": "Folder 1"
}
```

Returns created folder object.

Request example:

```
curl -H "Authorization: Token ${TOKEN}" -H "Content-Type: application/json" -X POST -d'{"name":"Folder 1", "assignees": ["user@acme.com"]}' "https://search.amazinghiring.com/api/v6/folders/"
```

Response example:

```json
{
    "assignees": ["user@acme.com"],
    "candidate_statuses": [
        {
            "id": 2,
            "name": "selected",
            "order": 0
        },
        {
            "id": 4,
            "name": "mailing_list",
            "order": 2
        },
        {
            "id": 6,
            "name": "interview",
            "order": 3
        },
        {
            "id": 8,
            "name": "offer",
            "order": 4
        },
        {
            "id": 9,
            "name": "unopened",
            "order": 0
        },
        {
            "id": 10,
            "name": "opened",
            "order": 1
        },
        {
            "id": 11,
            "name": "replied",
            "order": 2
        },
        {
            "id": 13,
            "name": "reject",
            "order": 5
        }
    ],
    "created_at": "2018-08-15T07:04:35.654679Z",
    "description": "",
    "id": 1,
    "modified_at": "2018-08-15T07:04:35.654860Z",
    "name": "Folder 1",
    "owner": {
        "email": "user@acme.com",
        "first_name": "User",
        "id": 1,
        "last_name": "User"
    },
    "status": "active"
}
```

### Update folder

**PATCH**	`/folders/{folder_id}/`

Updates existing folder.

Request body is json object with 2 parameters: `name` and `assignees`.

`name` - folder name. **Optional**.

`assignees` - array of user emails. **Optional**.

```json
{
    "assignees": [
        "user@acme.com",
        "user2@acme.com"
    ],
    "name": "Renamed Folder 1"
}
```

Returns created folder object.

Request example:

```
curl -H "Authorization: Token ${TOKEN}" -H "Content-Type: application/json" -X PATCH -d'{"name":"Renamed Folder 1", "assignees": ["user@acme.com", "user2@acme.com"]}' "https://search.amazinghiring.com/api/v6/folders/"
```

Response example:

```json
{
    "assignees": ["user@acme.com", "user2@acme.com"],
    "candidate_statuses": [
        {
            "id": 2,
            "name": "selected",
            "order": 0
        },
        {
            "id": 4,
            "name": "mailing_list",
            "order": 2
        },
        {
            "id": 6,
            "name": "interview",
            "order": 3
        },
        {
            "id": 8,
            "name": "offer",
            "order": 4
        },
        {
            "id": 9,
            "name": "unopened",
            "order": 0
        },
        {
            "id": 10,
            "name": "opened",
            "order": 1
        },
        {
            "id": 11,
            "name": "replied",
            "order": 2
        },
        {
            "id": 13,
            "name": "reject",
            "order": 5
        }
    ],
    "created_at": "2018-08-15T07:04:35.654679Z",
    "description": "",
    "id": 1,
    "modified_at": "2018-08-15T07:04:35.654860Z",
    "name": "Renamed Folder 1",
    "owner": {
        "email": "user@acme.com",
        "first_name": "User",
        "id": 1,
        "last_name": "User"
    },
    "status": "active"
}
```

### Delete folder

**DELETE**	`/folders/{folder_id}/`

Deletes existing folder.

Request example:

```
curl -H "Authorization: Token ${TOKEN}" -H "Content-Type: application/json" -X PATCH -d'{"name":"Renamed Folder 1", "assignees": ["user@acme.com", "user2@acme.com"]}' "https://search.amazinghiring.com/api/v6/folders/"
```

Response will be empty with HTTP code 200.

## Candidates

Candidate object links profile to folder with status. There will be 2 candidate objects if you will add 1 profile to 2 different folders.

* [Candidate object](#candidate-object)
* [**GET**	`/candidates/` Returns candidates list](#get-all-candidates)
* [**GET**	`/candidates/{candidate_id}/ Returns candidate object by id`](#get-candidate-by-id)
* [**POST**	`/candidates/ Creates candidate`](#create-candidate)
* [**PATCH**	`/candidates/{candidate_id}/ Updates candidate`](#update-candidate)
* [**DELETE**	`/candidates/{candidate_id}/ Deletes candidate`](#delete-candidate)



### Candidate object

```json
{
    "created_at": "2016-04-15T10:39:41.079931Z",
    "creator": 1,
    "folder_id": 1,
    "id": 1,
    "profile": 1,
    "status_id": 2
}
```

### Get all candidates

**GET**	`/candidates/`

Returns list of all candidates in your company

Request example:

```
curl -H "Authorization: Token ${TOKEN}" -H "Accept: application/json" "https://search.amazinghiring.com/api/v6/candidates/"
```

Response example:

```json
[
    {
        "created_at": "2016-04-15T10:39:41.079931Z",
        "creator": 1,
        "folder_id": 1,
        "id": 1,
        "profile": 1,
        "status_id": 2
    }
]
```

### Get candidate by id

**GET**	`/candidates/{candidate_id}/`

Returns candidate object by id

Request example:

```
curl -H "Authorization: Token ${TOKEN}" -H "Accept: application/json" "https://search.amazinghiring.com/api/v6/candidates/1/"
```

Response example:

```json
{
    "created_at": "2016-04-15T10:39:41.079931Z",
    "creator": 1,
    "folder_id": 1,
    "id": 1,
    "profile": 1,
    "status_id": 2
}
```

### Create candidate

**POST**	`/candidates/`

Adds profile to folder. Returns created candidate object

Request example:

```
curl -H "Authorization: Token ${TOKEN}" -H "Content-Type: application/json" -X POST -d'{"profile": 1, "folder_id": 1}' "https://search.amazinghiring.com/api/v6/candidates/"
```

Response example:

```json
{
    "created_at": "2016-04-15T10:39:41.079931Z",
    "creator": 1,
    "folder_id": 1,
    "id": 2,
    "profile": 1,
    "status_id": 2
}
```

### Update candidate

**PATCH**	`/candidates/{candidate_id}/`

Updates candidate object

Request example:

```
curl -H "Authorization: Token ${TOKEN}" -H "Content-Type: application/json" -X PATCH -d'{"status_id": 8}' "https://search.amazinghiring.com/api/v6/candidates/2/"
```

Response example:

```json
{
    "created_at": "2016-04-15T10:39:41.079931Z",
    "creator": 1,
    "folder_id": 1,
    "id": 2,
    "profile": 1,
    "status_id": 8
}
```

### Delete candidate

**DELETE**	`/candidates/{candidate_id}/`

Deletes candidate object

Request example:

```
curl -H "Authorization: Token ${TOKEN}" -X DELETE "https://search.amazinghiring.com/api/v6/candidates/2/"
```

Response will be empty with HTTP code 200.

