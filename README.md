# Welcome to the Cash Flow Minimizer System README !!

This system minimizes the **number of transactions** among multiple banks in the different corners of the world that use **different modes of payment**. There is one world bank (with all payment modes) to act as an intermediary between banks that have no common mode of payment.

# Getting Started

Let's take an example. say we have the following banks:
1. Bank_of_America (World bank)
2. Wells_Fargo
3. Royal_Bank_of_Canada
4. Westpac
5. National_Australia_Bank
6. Goldman_Sachs

Following are the payments to be done:\
&emsp;&emsp;&emsp;    **Debtor Bank**&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&nbsp;                **Creditor Bank** &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp; **Amount**
1. Goldman_Sachs   &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;             Bank_of_America &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&nbsp;&nbsp;&nbsp;             Rs 100
2. Goldman_Sachs   &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;              Wells_Fargo &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;                Rs 300
3. Goldman_Sachs   &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;              Royal_Bank_of_Canada  &emsp;&emsp;&emsp;&emsp;&nbsp;      Rs 100
4. Goldman_Sachs   &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;              Westpac &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&nbsp;&nbsp; Rs 100
5. National_Australia_Bank &emsp;&emsp;&nbsp;&nbsp;       Bank_of_America &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&nbsp;&nbsp;&nbsp; Rs 300
6. National_Australia_Bank &emsp;&emsp;&nbsp;&nbsp;       Royal_Bank_of_Canada &emsp;&emsp;&emsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Rs 100
7. Bank_of_America         &emsp;&emsp;&emsp;&emsp;&emsp;&nbsp;&nbsp;&nbsp;       Wells_Fargo &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&nbsp;&nbsp;&nbsp; Rs 400
8. Wells_Fargo             &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&nbsp;&nbsp;&nbsp;       Royal_Bank_of_Canada &emsp;&emsp;&emsp;&emsp;&nbsp; Rs 200
9. Royal_Bank_of_Canada    &emsp;&emsp;&nbsp;&nbsp;&nbsp;&nbsp;      Westpac &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&nbsp;&nbsp; Rs 500


This is represented below as a directed graph with the directed edge representing debts.
![image](https://user-images.githubusercontent.com/54183085/110007387-9c625100-7d40-11eb-9128-29073ea4b3f3.png)

**But there's a catch!!**
Each Bank only supports a set of modes of payments and can _make_ or _receive_ payments **only** via those. Only World Bank suppports **all** modes of payments.
In our current example we have only three payment modes :
1. Google_Pay
2. AliPay
3. Paytm

Following is the list of Banks and their supported payment modes :
1. Bank_of_America &emsp;&emsp;&emsp;&emsp;&nbsp;&nbsp;- &emsp; Google_Pay, AliPay, Paytm
2. Wells_Fargo &emsp;&emsp;&emsp;&emsp;&emsp;&nbsp;&nbsp;&emsp;&nbsp;- &emsp; Google_Pay, AliPay
3. Royal_Bank_of_Canada &nbsp;&emsp;&nbsp;&nbsp;&nbsp;- &emsp; AliPay
4. Westpac &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&nbsp;&nbsp;&nbsp;&nbsp; - &emsp; Google_Pay, Paytm
5. Goldman_Sachs &emsp;&emsp;&emsp;&emsp;&emsp;&nbsp;- &emsp; Paytm
6. National_Australia_Bank &nbsp;&nbsp;&nbsp;&nbsp;&nbsp; - &emsp; AliPay, Paytm  

To pick the first Bank, we calculate the **net amount** for every Bank by using the below formula and store them in list:

net amount = [Sum of all **credits**(_amounts to be received_)] - [Sum of all **debits**(_amounts to pay_)]

Now the idea is that we are finding the bank which has _minimum_ net amount(_max debtor_) (_say Bank X, net amount x_) and then finding the bank which has the _maximum_ net amount( _max creditor_) (_say Bank Y, net amount y_) and also has a common payment mode (_say M1_) with the former bank. Then we find _minimum_ of absolute value of x and y, lets call it z.\
Now X pays the amount z to Y. Then 3 cases may arrived:
1. If (magnitude of x) < y  =>  X is completely settled and so removed from the list.
2. If (magnitude of x) > y  =>  Y is completely settled and so removed from the list.
3. If (magnitude of x) = y  =>  X and Y both are completely settled and so both are removed from the list.

The same process is repeated for the remaining banks.\
For the current example, the transactions for minimum cash flow are as follows:

![image](https://user-images.githubusercontent.com/54183085/110007435-aab06d00-7d40-11eb-8e0c-ea5c7ec762a3.png)

So this is the required answer.

# How to Use?
This system is completely **menu-driven**. So when you will run the C++ Application, it will guide you and show you the final output.\
Below is the execution of our current example:
![image](https://user-images.githubusercontent.com/54183085/110011598-a33f9280-7d45-11eb-9499-a2868924cefd.png)

Thank you!!
Happy learning :)
