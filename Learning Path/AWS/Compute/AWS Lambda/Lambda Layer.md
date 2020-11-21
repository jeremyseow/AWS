# Lambda Layer
-  layer is a ZIP archive that contains libraries, a custom runtime, or other dependencies. With layers, you can use libraries in your function without needing to include them in your deployment package.

- Layers let you keep your deployment package small, which makes development easier. You can avoid errors that can occur when you install and package dependencies with your function code

- A function can use up to 5 layers at a time. The total unzipped size of the function and all layers can’t exceed the unzipped deployment package size limit of 250 MB.

- You can create layers, or use layers published by AWS and other AWS customers. Layers support resource-based policies for granting layer usage permissions to specific AWS accounts, AWS Organizations, or all accounts

- Layers are extracted to the /opt directory in the function execution environment. Each runtime looks for libraries in a different location under /opt, depending on the language
	- Structure your layer so that function code can access libraries without additional configuration.

![[Layer.png]]