# Test_Password_strength

#include <iostream>
#include <string>
#include <regex>
int testPasswordStrength(const std::string& password) {
    int score = 0;
    if (password.length() >= 8) {
        score++;
    }
    std::regex lowercase("[a-z]");
    std::regex uppercase("[A-Z]");
    std::regex digit("[0-9]");
    std::regex special("[^a-zA-Z0-9]");
    if (std::regex_search(password, lowercase) && std::regex_search(password, uppercase)) {
        score++;
    }
    if (std::regex_search(password, digit)) {
        score++;
    }
    if (std::regex_search(password, special)) {
        score++;
    }   
    return score;
}
std::string classifyStrength(int score) {
    if (score <= 2) {
        return "Weak";
    } else if (score <= 3) {
        return "Medium";
    } else if (score <= 4) {
        return "Strong";
    } else {
        return "Very Strong";
    }
}
int main() {
    std::string password;
    std::cout << "Enter your password: ";
    std::cin >> password;
    int score = testPasswordStrength(password);
    std::string strength = classifyStrength(score);
    std::cout << "Password strength: " << strength << std::endl;
    return 0;
}
