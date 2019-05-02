# pset1c
Introduction to Computer Science and Programming in Python

print("Veamos cuánto tendrías que ahorrar para conseguir esa casa en tan solo tres años.")

r = 0.04
total_cost = 1000000
semi_annual_raise = 0.07
down_payment = total_cost * 0.25
set_annual_salary =  float(input("Okay, cuánto ganas al año? "))
min_portion_saved = 0
max_portion_saved = 10000

num_steps = 0
current_savings = 0
guess = 5000

while abs(current_savings-down_payment)>=100:

    months=0
    current_savings=0
    annual_salary=set_annual_salary
    monthly_salary=annual_salary/12
    while months<36:
      current_savings*=(1+r/12)
      current_savings+=annual_salary/12 * guess/10000

      if months>0 and months % 6==0:
         annual_salary+=annual_salary*semi_annual_raise 
      months+=1


    if current_savings<down_payment:
            min_portion_saved=guess
    else:
            max_portion_saved=guess
        
    guess=(max_portion_saved+min_portion_saved)//2

    num_steps+=1

    if guess>=9999 and current_savings<down_payment:
       print("Lo siento, no llegas ni de coña brother")
       break

if abs(down_payment - current_savings) <= 100:
    print("La tasa de ahorro correcta es: ", guess / 10000)
    print("Steps in the bisection search: ", num_steps)    
    
