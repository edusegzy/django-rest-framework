# Schema

## Generating an OpenAPI Schema

### Static

If your schema is static, you can use the `generateschema` management command:

```bash
./manage.py generateschema > openapi-schema.yml
```

### Dynamic

If you require a dynamic schema, because foreign key choices depend on database values, for example, you can route a `SchemaView` that will generate and serve you schema on demand.

In `urls.py`:

```python
from rest_framework.schemas import get_schema_view()

urlpatterns = [
    # ...
    # Use the `get_schema_view()` helper to add a `SchemaView` to project URLs.
    #   * `title` and `description` parameters are passed to `SchemaGenerator`.
    #   * Provide view name for use with `reverse()`.
    path('openapi', get_schema_view(
        title="Your Project",
        description="API for all things …"
    ), name='openapi-schema'),
    # ...
]
```

#### `get_schema_view()`

* ...

* ...

* ...



## Customizing Schema Generation

### Schema Level Customization

### Per-View Customization

* Subclass `rest_framework.schemas.openapi.AutoSchema`.
* Override `get_operations()`.