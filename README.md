# Water-jug-problem
# # # Aditya Sharma

# # # <CASE STUDY 2>
# # # You are given three jugs with capacities A, B, and C liters, respectively. Initially, jugs A and B
# # # are empty, and jug C is full. Your task is to measure exactly T liters of water using these jugs. 
# # # You can fill a jug, empty a jug, or pour water from one jug to another until either the source jug 
# # # is empty or the destination jug is full.
# # # Test Cases:
# # # 1. Case 1: A=3, B=5, C=8, T=4
# # # 2. Case 2: A=4, B=6, C=10, T=7
# # # 3. Case 3: A=5, B=7, C=11, T=8 


def water_jug_problem(jugA_capacity, jugB_capacity, jugC_capacity, target_amount):
    jugA_current = 0  
    jugB_current = 0  
    jugC_current = jugC_capacity
    jugT_current = 0  

    print(f"Inital State: JugA: {jugA_current}/{jugA_capacity}    Jug B: {jugB_current}/{jugB_capacity} Jug C: {jugC_current}/{jugC_capacity} Jug T: {jugT_current}/{target_amount}")

    def pour(from_jug, to_jug, max_to_jug):
        amount = min(from_jug, max_to_jug - to_jug)
        to_jug += amount
        from_jug -= amount
        return from_jug, to_jug

    while jugT_current != target_amount:
        jugC_current, jugT_current = pour(jugC_current, jugT_current, target_amount)

        if jugT_current == target_amount:
            break

        if jugC_current == 0:
            jugC_current = jugC_capacity

        jugA_current, jugC_current = pour(jugA_current, jugC_current, jugA_capacity)

        jugB_current, jugC_current = pour(jugB_current, jugC_current, jugB_capacity)

        if jugA_current == 0 and jugB_current == 0 and jugC_current != 0:
            print("cacnot be reached")
            break

    print("Target reached")
    print(f"Final State: Jug A: {jugA_current}/{jugA_capacity}    Jug B: {jugB_current}/{jugB_capacity}    Jug C: {jugC_current}/{jugC_capacity}    Jug T: {jugT_current}/{target_amount}")


print("Case 1:")
water_jug_problem(3, 5, 8, 4)
print("\nCase 2:")
water_jug_problem(4, 6, 10, 7)
print("\nCase 3:")
water_jug_problem(5, 7, 11, 8)
