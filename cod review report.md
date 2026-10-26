| Line Number | Defect Type | Why It Is a Problem | Proposed Fix | Severity |
| --- | --- | --- | --- | --- |
| 47 | Control flow | Assignment (=) used instead of comparison (==); overwrites the id and always returns the first monster | Change to monsters[i]->id == id | High |
| 41 | Array bounds | spawnMonster() has no capacity check; writing past monsters[4] corrupts memory | Check monsterCount < MAX_MONSTERS before adding and return false when full | Critical |
| 119 | Array bounds | main() spawns a 6th monster into an array of size 5 | Increase MAX_MONSTERS or remove the extra spawn | Critical |
| 64 | Loop | Condition i <= monsterCount reads one element past the last valid monster | Change to i < monsterCount | Critical |
| 77 | Initialization | sum is never initialized, so the average is garbage | Initialize with double sum = 0.0 | High |
| 80 | Arithmetic | Division by zero when monsterCount is 0; double result silently truncated to int | Return 0 if monsterCount is 0; return double or round explicitly | Medium |
| 31 | Initialization | monsters[] pointers are left uninitialized in the constructor | Initialize the array to nullptr in the constructor | Low |
| 55 | Arithmetic | unsigned int dmg makes health - dmg unsigned, so the < 0 check is never true and values wrap | Use int and check m->health - damage < 0, clamping health to 0 | High |
| 56 | Pointer | m can be nullptr when the id is not found, and is dereferenced | Check if (!m) before use and return an error value | Critical |
| 123 | Function call | attackMonster(99, 20) uses an id that does not exist | Use a valid id or handle the not-found case | Medium |
| 70 | Pointer | Returns a reference to local variable label, which is destroyed on return (dangling reference) | Return std::string by value | Critical |
| 72 | Pointer | m can be nullptr and is dereferenced without a check | Check m before use and return an empty or default label | High |
| 85 | Pointer | Monster deleted but its pointer stays in monsters[], so the destructor deletes it again | Remove the pointer from the array (shift the rest down) and decrement monsterCount | Critical |
| 86 | Pointer | m->name is read after delete m (use after free) | Print the name before deleting | Critical |
| 91 | Arithmetic | Integer division truncates before conversion to double; attack * armorPercent can overflow | Use attack * armorPercent / 100.0 | Medium |
| 94 | Control flow | No return value when score is 100 or less (undefined behavior) | Add a final else that returns 3 | High |
| 102 | Pointer | Raw char buffer of 10 bytes with no need for manual memory | Use std::string name | Medium |
| 103 | Initialization | health is uninitialized if cin >> health fails | Initialize with int health = 0 and check the stream state | Medium |
| 105 | Array bounds | cin >> name into a 10-char buffer can overflow | Read into std::string | Critical |
| 109 | Pointer | Memory from new[] released with delete instead of delete[] | Use std::string, or delete[] name | High |
| 121 | Pointer | bonus is allocated with new and never freed (memory leak) | Delete it, or use a stack object or smart pointer | Low |
| 133 | Pointer | Game has no copy constructor, so the copy shares pointers and both destructors delete the same monsters | Delete the copy operations, or implement a deep copy (rule of three) | Critical |
