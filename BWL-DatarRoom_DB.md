
### **User**

| **Name**       | **Type**  | **Notes**                                                   |
| -------------- | --------- | ----------------------------------------------------------- |
| `userId`       | `string`  | **Primary Key**. Unique ID for each user                    |
| `firstName`    | `string`  | First name                                                  |
| `lastName`     | `string`  | Last name                                                   |
| `email`        | `string`  | **Unique**. User's email                                    |
| `profilePicUrl`| `string`  | URL to User's picture                                       |
| `isActive`     | `boolean` | Default: `true`                                             |
| `isVerified`   | `boolean` | Default: `false`                                            |
| `lastLogin`    | `Date`    | Timestamp of the last login                                 |
| `createdAt`    | `Date`    | **Not Null**. Timestamp when the user was created           |
| `updatedAt`    | `Date`    | **Not Null**. Timestamp when the user was last updated      |

### **Documents**

| **Name**          | **Type**  | **Notes**                                                   |
| ----------------- | --------- | ----------------------------------------------------------- |
| `fileId`          | `string`  | **Primary Key**. Unique ID identifying the file             |
| `fileName`        | `string`  | Name of the file                                            |
| `type`            | `string`  | File type / extension                                       |
| `fileDirectory`   | `string`  | Directory where the file is located                         |
| `fileSize`        | `int`     | Size of the file in bytes                                   |
| `mimeType`        | `string`  | MIME type of the file                                       |
| `createdBy`       | `string`  | **Foreign Key**. References `User.userId`                   |
| `createdAt`       | `Date`    | **Not Null**. Creation time                                 |
| `updatedAt`       | `Date`    | **Not Null**. Last update time                              |
| `updatedBy`       | `string`  | **Foreign Key**. References `User.userId`                   |
| `totalViews`      | `int`     | Total number of times the file was viewed                   |
| `uniqueViews`     | `int`     | Number of unique viewers of the file                        |

### **Links**

| **Name**          | **Type**  | **Notes**                                                   |
| ----------------- | --------- | ----------------------------------------------------------- |
| `linkId`          | `string`  | **Primary Key**. Unique ID for the link                     |
| `fileId`          | `string`  | **Foreign Key**. References `Documents.fileId`              |
| `linkName`        | `string`  | Name of the link                                            |
| `linkUrl`         | `string`  | URL of the link                                             |
| `isPublic`        | `boolean` | Indicates if the link is public                             |
| `emailRequired`   | `boolean` | Indicates if an email is required for download              |
| `canExpire`       | `boolean` | Indicates if the link can expire                            |
| `expirationTime`  | `Date`    | Expiration date of the link (nullable)                      |
| `updatedAt`       | `Date`    | **Not Null**. Last update time                              |
| `createdAt`       | `Date`    | **Not Null**. Creation time                                 |
| `createdBy`       | `string`  | **Foreign Key**. References `User.userId`                   |

### **DataRooms**

| **Name**          | **Type**  | **Notes**                                                   |
| ----------------- | --------- | ----------------------------------------------------------- |
| `folderId`        | `string`  | **Primary Key**. Unique ID for the folder                   |
| `folderName`      | `string`  | Name of the folder                                          |
| `folderLocation`  | `string`  | Location of the folder                                      |
| `updatedAt`       | `Date`    | **Not Null**. Last update time                              |
| `updatedBy`       | `string`  | **Foreign Key**. References `User.userId`                   |
| `createdAt`       | `Date`    | **Not Null**. Creation time                                 |
| `createdBy`       | `string`  | **Foreign Key**. References `User.userId`                   |

### **AccessLogs**

| **Name**          | **Type**  | **Notes**                                                   |
| ----------------- | --------- | ----------------------------------------------------------- |
| `logId`           | `string`  | **Primary Key**. Unique ID for each access log              |
| `linkId`          | `string`  | **Foreign Key**. ID of the link accessed                    |
| `userId`          | `string`  | **Foreign Key**. ID of the user who accessed the link       |
| `accessTime`      | `Date`    | **Not Null**. Timestamp when the link was accessed          |
| `ipAddress`       | `string`  | IP address of the user who accessed the link                |
