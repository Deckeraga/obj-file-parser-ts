# obj-file-parser-ts
This is a fork of [obj-file-parser](https://github.com/WesUnwin/obj-file-parser) converted to typescript.

## Additional Fork Features
  * Types

## Installation
```sh
npm i obj-file-parser-ts
```

## Usage

```javascript
const OBJFile = require('obj-file-parser');

const fileContents =
  'v 0 0 0 \n' +
  'v 0 1 0 \n' +
  'v 1 0 0 \n' +
  'f 1 2 3';

const objFile = new OBJFile(fileContents);

const output = objFile.parse(); // see description below
```


## Output
The extracted model data and list of material library references
are returned in the following format:

```
{
  models: [
    {
      name: 'unit_cube',
      vertices: [
        { x: 1.0, 2.0, 3.0 },
        ...
      ],
      textureCoords: [
        { u: 1.0, v: 2.0, w: 3.0 },
        ...
      ],
      vertexNormals: [
        { x: 1.0, y: 2.0, z: 3.0 },
        ...
      ],
      faces: [
        {
          material: 'brick',
          group: 'group1',
          smoothingGroup: 0,
          vertices: [
            { vertexIndex: 1, textureCoordsIndex: 1, vertexNormalIndex: 1 },
            ...
          ]
        }
      ]
    },
    {
      ...
    }
  ],

  materialLibraries: [
    'mat_lib1.mtl',
    ...
  ]
}
```
