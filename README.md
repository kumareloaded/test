Certainly! Here's an example of a full Java class that demonstrates how you can update the `@ExternalDocumentation` annotation with dynamic values using a simple test scenario:

```java
import io.swagger.annotations.ExternalDocumentation;
import io.swagger.annotations.Api;
import io.swagger.annotations.ApiOperation;

@Api(value = "Your API", externalDocs = @ExternalDocumentation(value = "Placeholder URL", description = "Placeholder Description"))
public class YourController {

    @ApiOperation(value = "Your API Endpoint")
    public void yourApiEndpoint() {
        // Your endpoint implementation
    }

    public void updateExternalDocs(String dynamicUrl, String dynamicDescription) {
        Api apiAnnotation = YourController.class.getAnnotation(Api.class);
        ExternalDocumentation externalDocs = apiAnnotation.externalDocs();

        // Modify the values with dynamic values
        ExternalDocumentation modifiedExternalDocs = new ExternalDocumentation()
                .value(dynamicUrl)
                .description(dynamicDescription);

        apiAnnotation.externalDocs(modifiedExternalDocs);
    }

    public static void main(String[] args) {
        YourController controller = new YourController();

        // Original Swagger documentation
        SwaggerUtils.generateSwaggerDocumentation(controller.getClass());

        // Update external docs with dynamic values
        controller.updateExternalDocs("https://example.com/docs", "Dynamic Documentation");

        // Updated Swagger documentation
        SwaggerUtils.generateSwaggerDocumentation(controller.getClass());
    }
}
```

In this example, we have a `YourController` class that represents your API controller. The class is annotated with `@Api` to define the API and includes an `@ExternalDocumentation` annotation with placeholder values for the URL and description.

The `updateExternalDocs` method allows you to update the `@ExternalDocumentation` annotation with dynamic values. In this case, it takes in the dynamic URL and description and modifies the annotation accordingly.

The `main` method demonstrates how you can generate Swagger documentation using a utility class called `SwaggerUtils`. In this example, we assume the existence of a `SwaggerUtils.generateSwaggerDocumentation` method that takes the controller class as a parameter and generates the Swagger documentation. You would need to provide the implementation for this utility class or utilize an existing Swagger library that provides such functionality.

By running this example, you'll see the Swagger documentation being generated twice: once with the original placeholder values and then with the updated dynamic values applied through the `updateExternalDocs` method.

Remember to adjust the code according to your specific needs and any existing Swagger libraries or utilities you are using.
