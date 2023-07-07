# acquire_per_file_info_obj

This function populate a fileinfo field on the `obj` parameter. It will never be invoked on a non-dynamic SELF.

## Parameters

1. `imgp`: A pointer to `image_params`.
2. `obj`: A pointer to `Obj_Entry`.

## Returns

- `i32`: zero on success or `errno` in case of error.

## Locations

| Version | Offset     |
| ------- | ---------- |
| 9.0     | 0x0021A680 |
