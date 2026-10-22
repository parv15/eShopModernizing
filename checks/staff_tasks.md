# Catalog app: everyday staff tasks to check after migration

Staff use this app to manage the shop's product catalog. Run every task below on the old app first and note what you see, then run the same task on the migrated app. A task passes when the result matches.

The old app starts with 12 catalog items, 5 brands and 4 types.

| # | Task | Where | What to check |
| --- | --- | --- | --- |
| 1 | Open the catalog list | Home page (`/`) | 10 items on the first page, each with picture, name, brand, type, price and stock levels; the pager reads "Showing 10 of 12 products - Page 1 - 2" |
| 2 | Move to the next page | Next, under the list | Page 2 shows the remaining 2 items; the pager still reads "Showing 10 of 12 products - Page 2 - 2" (it shows the page size, not the count on the page, and the migrated app should keep or deliberately fix this) |
| 3 | Show 5 items per page | `/Catalog/Index?pageSize=5` | 5 items per page and 3 pages in total |
| 4 | Open an item's details | Details on ".NET Bot Black Hoodie" | Name, description, brand .NET, type T-Shirt, price 19.50, stock 100 and the picture all show |
| 5 | See an item's picture on its own | `/items/1/pic` | The hoodie picture loads as an image |
| 6 | Add a new item | Create | Fill in name, price 24.99, brand, type and stock levels, save, and the item appears in the list |
| 7 | Reject a bad price | Create | Price 12.345 is refused with the "maximum two decimals" message |
| 8 | Reject missing name | Create | Saving with no name is refused |
| 9 | Edit an item | Edit on the item from task 6 | Change price to 21.00 and stock to 40, save, and the list shows the new values |
| 10 | Delete an item | Delete on the item from task 6 | Confirm, and the item is gone from the list |
| 11 | List brands through the API | `GET /api/brands` | JSON list of the 5 brands |
| 12 | Get one brand through the API | `GET /api/brands/1` | JSON for that single brand |
| 13 | Download brands as a file | `GET /api/files` | A file downloads (the old app sends brands in a binary format) |
| 14 | Session details in the footer | Any page | The footer shows the server name and when the session started |

Task 13 depends on a .NET Framework feature that modern .NET no longer supports, so the team decides what this endpoint should return before the migration (see the Living Spec).
