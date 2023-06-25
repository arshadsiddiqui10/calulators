def calculate_emi(loan_amount, interest_rate, repayment_tenure):
    r = interest_rate / (12 * 100)  # Monthly interest rate
    n = repayment_tenure * 12  # Total number of monthly installments

    emi = (loan_amount * r * ((1 + r) ** n)) / (((1 + r) ** n) - 1)  # Calculate EMI

    return round(emi, 2)


def calculate_interest_saved(loan_amount, interest_rate, repayment_tenure, savings_balance):
    emi_without_overdraft = calculate_emi(loan_amount, interest_rate, repayment_tenure)

    loan_interest_without_overdraft = emi_without_overdraft * (repayment_tenure * 12) - loan_amount  # Calculate total interest without overdraft

    # Calculate EMI with overdraft
    emi_with_overdraft = calculate_emi(loan_amount - savings_balance, interest_rate, repayment_tenure)

    loan_interest_with_overdraft = emi_with_overdraft * (repayment_tenure * 12) - (loan_amount - savings_balance)  # Calculate total interest with overdraft

    interest_saved = loan_interest_without_overdraft - loan_interest_with_overdraft  # Calculate interest saved

    return round(interest_saved, 2), emi_without_overdraft, emi_with_overdraft,loan_interest_without_overdraft,loan_interest_with_overdraft


# Example usage
loan_amount = float(input("Enter the loan amount: "))
interest_rate = float(input("Enter the interest rate (%): "))
repayment_tenure = int(input("Enter the repayment tenure (in years): "))
savings_balance = float(input("Enter the savings balance: "))
monthly_deposit = float(input("Enter the monthly_deposit in savings account: "))

print("Month\tEMI without overdraft\tEMI with overdraft\tInterest saved")
interest_saved_total: float = 0
loan_interest_without_overdraft_total: float = 0
loan_interest_with_overdraft_total: float = 0
for month in range(1, repayment_tenure * 12 + 1):

    interest_saved, emi_without_overdraft, emi_with_overdraft,loan_interest_without_overdraft,loan_interest_with_overdraft = calculate_interest_saved(
        loan_amount, interest_rate, repayment_tenure, savings_balance
    )
    if emi_with_overdraft <= 0:
      break
    print(f"{month+1}\t{round(emi_without_overdraft, 2)}\t\t\t{round(emi_with_overdraft, 2)}\t\t\t{interest_saved}")
    #print("EMI without overdraft: ", round(emi_without_overdraft, 2))
    #print("EMI with overdraft: ", round(emi_with_overdraft, 2))
    #print("Interest saved for the complete loan tenure: ", round(interest_saved, 2))
    savings_balance += monthly_deposit
    interest_saved_total += interest_saved
print("Total Interest saved for the complete loan tenure: ", round(interest_saved_total, 2))
print("Total Interest for the complete loan tenure without OD: ", round(loan_interest_without_overdraft_total, 2))
print("Total Interest for the complete loan tenure with OD: ", round(loan_interest_with_overdraft_total, 2))
