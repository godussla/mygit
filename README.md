import random


def get_computer_choice():
    return random.choice(['가위', '바위', '보'])


def determine_winner(user_choice, computer_choice):
    if user_choice == computer_choice:
        return '무승부'
    elif (user_choice == '가위' and computer_choice == '보') or \
            (user_choice == '보' and computer_choice == '바위') or \
            (user_choice == '바위' and computer_choice == '가위'):
        return '사용자 승리'
    else:
        return '컴퓨터 승리'


def main():
    wins = 0
    losses = 0
    draws = 0

    while True:
        user_input = input("가위, 바위, 보 중에서 선택하세요: ").strip().lower()

        if user_input not in ['가위', '바위', '보']:
            print("유효한 값이 아닙니다. 다시 입력하세요.")
            continue

        user_choice = user_input
        computer_choice = get_computer_choice()
        print(f"사용자: {user_choice} 컴퓨터: {computer_choice}")

        result = determine_winner(user_choice, computer_choice)

        if result == '사용자 승리':
            wins += 1
        elif result == '컴퓨터 승리':
            losses += 1
        else:
            draws += 1

        print(result)

        play_again = input("다시 시작하겠습니까? (예/아니오): ").strip().lower()

        if play_again != '예' and play_again != 'yes':
            break

    print(f"게임을 끝냅니다\n승: {wins} 패: {losses} 무승부: {draws}")


if __name__ == "__main__":
    main()

