# Multiple Apps

This example loads a different task pane depending on the name of the workbook.

To try it out, replace the task pane endpoint in app/routers/taskpane.py with the following code:

```python
@router.get("/taskpane")
async def taskpane(request: Request, app: str = None):
    if not app:
        template = "examples/multi_app/taskpane_loader.html"
    elif app == "1":
        template = "examples/multi_app/taskpane1.html"
    elif app == "2":
        template = "examples/multi_app/taskpane2.html"

    return TemplateResponse(
        request=request,
        name=template,
        context={"settings": settings},
    )
```

The sample also depends on code in:

- `app/static/js/examples.js`