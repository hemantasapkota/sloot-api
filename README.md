sloot-api
=========

API for loading Sloot Editor Screen and Entities file.

Load Screen File (*.cgs)
========================

```Java
File file = new File("SpritesDemo/screens/Screen1.cgs");
//Use your favorite way to load the contents of the file in a byte array
byte[] barr = ByteStreams.toByteArray(new FileInputStream(file)); //ByteStreams is a part of [Guava](https://code.google.com/p/guava-libraries/)

//Google Protobuf generated API
		CGScreenModel screenModel = CGScreenModel.parseFrom(barr);
		
		/**
		ScreenModel has layers.
		  Each Layer has many shapes.
		    Each Shape has host of properties.
		
		ScreenModel also has preferences.
		For more details check out the proto file that describes it all. 
		[ScreenModel.proto](https://github.com/hemantasapkota/sloot-editor/blob/master/com.laex.cg2d.shared/src/com/laex/cg2d/model/ScreenModel.proto)
		*/

		for (CGLayer layer : screenModel.getLayersList()) {

			for (CGShape shape : layer.getShapeList()) {

				System.err.println(shape.getId());

			}

		}
```
