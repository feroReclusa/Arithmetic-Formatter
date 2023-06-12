# Arithmetic-Formatter
test free camp
def arithmetic_arranger(problems, show_answers=False):
    # Check if the number of problems exceeds the limit
    if len(problems) > 5:
        return "Error: Too many problems."

    line1 = line2 = line3 = line4 = ""
    arranged_problems = []

    for problem in problems:
        operand1, operator, operand2 = problem.split()

        # Check for valid operators
        if operator not in ['+', '-']:
            return "Error: Operator must be '+' or '-'."

        # Check if operands are valid integers
        if not operand1.isdigit() or not operand2.isdigit():
            return "Error: Numbers must only contain digits."

        # Check if operands are within the range of 4 digits
        if len(operand1) > 4 or len(operand2) > 4:
            return "Error: Numbers cannot be more than four digits."

        width = max(len(operand1), len(operand2)) + 2
        line1 += operand1.rjust(width) + "    "
        line2 += operator + operand2.rjust(width - 1) + "    "
        line3 += "-" * width + "    "

        if show_answers:
            if operator == '+':
                result = str(int(operand1) + int(operand2))
            else:
                result = str(int(operand1) - int(operand2))
            line4 += result.rjust(width) + "    "

    arranged_problems.extend([line1.rstrip(), line2.rstrip(), line3.rstrip(), line4.rstrip()])
    return "\n".join(arranged_problems)
