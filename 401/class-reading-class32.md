
# **Reading Notes: Permissions & Postgresql**


## Why are these reading important?

```
```


---

## [**DRF Permissions:**](https://www.django-rest-framework.org/api-guide/permissions/)


---

## [**Review SQL Prework:**](https://codefellows.github.io/common_curriculum/prework/SQL)


---

## [**Classy Django REST:**](http://www.cdrf.co/)


---

## [**DRF Generic Views:**](https://www.django-rest-framework.org/api-guide/generic-views/)


---

## READING QUESTIONS:


	1. Prompt: What are the key components and purpose of Django Rest Framework (DRF) permissions, and how do they help in securing an API?

		Solution: The key components of the DRF permissions are implemented through the use of classes such as AllowAny, IsAuthenticated, IsAdminUser, and IsAuthenticatedOrReadOnly. The classes and or their methods can be used or modified to control client access and actions at a global level, at the view level, or at an object level.

	2. Prompt: In SQL, what is the purpose of the SELECT statement, and how would you use it to retrieve all columns from a table called ‘employees’?

		Solution: The SELECT keyword is used to retrieve data from a database. An examples of how to use it to select all the columns from an 'employees' table is as follows.

```SQL
SELECT * FROM employees;
```


	3. Prompt: Can you explain the role of DRF Generic Views and provide examples of their usage in building a RESTful API?

		Solution: DRF Generic Views are pre-defined views available with DRF to simplify CRUD operations in a REST API.


```python
from rest_framework import permissions, generics
from snacks.models import Snack
from .serializer import SnackSerializer


class SnacksListView(generics.ListAPIView):
    queryset = Snack.objects.all()
    serializer_class = SnackSerializer


class SnacksListViewCreate(generics.ListCreateAPIView):
    permission_classes = (permissions.IsAuthenticated,)
    queryset = Snack.objects.all()
    serializer_class = SnackSerializer


class SnackDetailed(generics.RetrieveUpdateDestroyAPIView):
    permission_classes = (permissions.IsAuthenticated,)
    queryset = Snack.objects.all()
    serializer_class = SnackSerializer
```

---

## **What I want to learn more about:**

	1. I am curious as to the tradeoffs between DRF permissions at the view, model, object, vs the global level?

---
---
---
