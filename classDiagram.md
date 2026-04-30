```mermaid
classDiagram
    class BankUI {
        +main() void
        +displayMenu() void
    }

    class User {
        -id : String
        -pw : String
        -name : String
        -phone : String
        -address : String
        +registerUser(id: String, pw: String, name: String, phone: String, address: String) User
        +updateUser(name: String, phone: String, address: String) void
        +deleteUser(id: String) void
        +searchUser(id: String) User
    }

    class Account {
        -number : String
        -balance : long
        +deposit(id: String, amount: long) void
        +withdraw(id: String, amount: long) void
        +transfer(id: String, targetAccountNumber: String, amount: long) void
        -computeBalance() long
    }

    %% 관계 설정
    %% User 1명당 Account는 1개 이상 (1..*)
    %% Account에서 User로의 사용자 조회 목적 연관관계
    User "1" <-- "1..*" Account : 사용자 조회

    %% BankUI가 Account를 사용하는 의존관계
    BankUI ..> Account : 의존(Dependency)
