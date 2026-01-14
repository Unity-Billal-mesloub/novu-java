# UploadTranslationsResponseDto


## Fields

| Field                                     | Type                                      | Required                                  | Description                               | Example                                   |
| ----------------------------------------- | ----------------------------------------- | ----------------------------------------- | ----------------------------------------- | ----------------------------------------- |
| `totalFiles`                              | *double*                                  | :heavy_check_mark:                        | Total number of files processed           | 3                                         |
| `successfulUploads`                       | *double*                                  | :heavy_check_mark:                        | Number of files successfully uploaded     | 2                                         |
| `failedUploads`                           | *double*                                  | :heavy_check_mark:                        | Number of files that failed to upload     | 1                                         |
| `errors`                                  | List\<*String*>                           | :heavy_check_mark:                        | List of error messages for failed uploads | [<br/>"Invalid JSON in file: es-ES.json"<br/>] |