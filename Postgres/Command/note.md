## Constraints check

```bash
docker exec -it postgres psql -U postgres -d coffee_chain

\d products.catalog

Table "products.catalog"
Column | Type | Nullable |
----------------+------------------------+----------+
id | integer | not null |
name | character varying(100) | not null |
description | text | not null |
category | text | |
price | numeric(10,2) | |
stock_quantity | integer | |

Indexes:
    "catalog_pkey" PRIMARY KEY, btree (id)
Check constraints:
    "catalog_category_check" CHECK (category = ANY (ARRAY['coffee'::text,
        'mug'::text, 't-shirt'::text]))
    "catalog_stock_quantity_check" CHECK (stock_quantity >= 0)
```