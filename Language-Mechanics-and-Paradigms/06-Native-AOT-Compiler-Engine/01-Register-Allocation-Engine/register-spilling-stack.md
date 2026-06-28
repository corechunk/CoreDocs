# 📦 Register Spilling Mechanics & Stack Reservation

## 1. Register Pressure & Spilling
When active variables outnumber physical hardware registers, the allocator selects candidate variables to "spill" into memory.

## 2. Stack Slot Reservation
Spilled values emit store instructions (`mov [rbp - offset], reg`) to save data into reserved stack frame memory slots, reloading them into registers (`mov reg, [rbp - offset]`) immediately before subsequent reads.
