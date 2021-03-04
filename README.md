# Welcome to the Cash Flow Minimizer System README !!

This system minimizes the **number of transactions** among multiple banks in the different corners of the world that use **different modes of payment**. There is one world bank (with all payment modes) to act as an intermediary between banks that have no common mode of payment.

# Getting Started

Let's take an example. We have World Bank, Bank B, Bank C, Bank D and Bank E. Some amounts are needed to be payed. Bank B owes World Bank Rs 300 , Bank C owes World Bank Rs 700, Bank D owes Bank B Rs 500 and Bank E owes Bank B Rs 500. This is represented below as a directed graph with the directed edge representing debts.

![image](https://user-images.githubusercontent.com/54183085/109980523-04576e00-7d26-11eb-848b-10167950a7a0.png)

**But there's a catch!!**
Each Bank only supports a set of modes of payments and can _make_ or _receive_ payments **only** via those. Only World Bank suppports **all** modes of payments.\ 
In our current example we have only two payment modes :
1. Google Pay
2. PayTM

Following is the list of Banks and their supported payment modes :
- World Bank - Google Pay, PayTM
- Bank B     - Google Pay
- Bank C     - Google Pay
- Bank D     - PayTM
- Bank E     - PayTM   

To pick the first Bank, we calculate the **net amount** for every Bank by using the below formula:\\
net amount = [Sum of all **credits**(_amounts to be received_)] - [Sum of all **debits**(_amounts to pay)]\\
Now the idea is that we are finding the bank which has _minimum_ net amount(_max debtor_) (_say Bank X, net amount x_) and then finding the bank which has the _maximum_ net amount( _max creditor_) (_say BanK Y, net amount y_) and also has a common payment mode (_say M1_) with the former bank. Then we find _minimum_ of absolute value of x and y, lets call it z.\
Now X pays the amount z to Y. Then 3 cases may arrived:
1. If (magnitude of x) < y  =>  X is completely settled and so removed from the list.
2. If (magnitude of x) > y  =>  Y is completely settled and so removed from the list.
3. If (magnitude of x) = y  =>  X and Y both are completely settled and so bot are removed from the list.

The same process is repeated for the remaining banks.\
For the current example, the transactions for minimum cash flow are as follows:

![image](https://user-images.githubusercontent.com/54183085/109980573-0f120300-7d26-11eb-81c2-ca9e31b07329.png)

So this is the required answer.

# How to Use?
This system is completely **menu-driven**. So when you will run the C++ Application, it will guide you and show you the final output.\
Below is the execution of our current example:
![image](https://user-images.githubusercontent.com/54183085/109976164-77121a80-7d21-11eb-9c84-ce99a843d6ea.png)

Thank you!!
