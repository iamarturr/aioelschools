# Asynchronous wrapper for Elschool API
My first asynchronous wrapper for Elschool API with typing support (ツ)

[![PyPI](https://img.shields.io/pypi/v/aioelschools)](https://pypi.org/project/aioelschools/)
![code-size](https://img.shields.io/github/languages/code-size/iamarturr/aioelschools)
![repo-size](https://img.shields.io/github/repo-size/iamarturr/aioelschools)


## Docs
You can see all returned responses in [models](https://github.com/iamarturr/aioelschool/blob/main/aioelschools/models/models.py)

And don't forget to use IDE for easy coding:

![alt text](https://raw.githubusercontent.com/iamarturr/aioelschool/main/image/1.jpg)

## Installation
Before install wrapper make sure you have downloaded [**Python 3.7+**](https://www.python.org/downloads/)

**Windows**

    pip install -U aioelschools
    

## Examples

### Using a method to get a token

```python
from aioelschools import ElschoolAPI
import asyncio


api = ElschoolAPI()


async def main():
    result = await api.login.token_get(login="Login", password="Password")
    print(result)
    # status='ok' error=Error(code='200', description='ok') result=UsersFull(Id=12345, Login='Login', Password='', Email='', INN='', SNILS='', BornDate='01/01/22 12:00:00 AM', Photo='', FirstName='Firstname', LastName='Lastname', MiddleName='Middlename', Token='eyJhbGciOiEFUzI1ertNiIsIneReegJ9.eyJ1c2VySWQiOiIywfwfc2MjgzIiwiY2hpbGRettetegjI3NjI4MyIsImRlcGFydG1lbnRMaXN0IjoiMTYwMzY0IiwibmJmIjoxNjUzNTkxNjAwLCJleHAiOjE2NTQ0NTU2MDAsImlhdCI6MTY1MFENIOniqfejoiY29ycC5icnNjLnJ1In0.oeqgingqpiqgieiqgeipnqgeip', Roles=[UsersRoles(Id=1234, RoleId=8, UserId=12345, RoleName='Учащийся', EntityType='Department', EntityName='EntityName', ChildId=None)])

asyncio.run(main())

```

### Catching Exceptions
Generic-type catching errors. Slightly modified class [CodeException](https://github.com/vkbottle/vkbottle/blob/77cf27c082d5da1aec4252e968bae712b633ce98/docs/low-level/exception_handling/code-exception.md) from framework [vkbottle](https://github.com/vkbottle/vkbottle/)

```python
from aioelschools import ElschoolAPI, APIError
import asyncio


api = ElschoolAPI()


async def main():
    try:
        await api.login.token_get(login="LOGIN34", password="PASSWORD")
    except APIError[2] as e:
        print(f"User is not active: {e.description}")
    except APIError[5] as e:
        print(f"Incorrect password: {e.description}")
    except APIError as e:
        print(f"Error '{e.description}' with code {e.code}")


asyncio.run(main())
```

## License
* AioElschools: ![license](https://img.shields.io/github/license/iamarturr/aioelschools)
