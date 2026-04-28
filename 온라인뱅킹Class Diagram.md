```mermaid
classDiagram
    class 고객정보 {
        -주민번호:String
        -성명:String
        +고객등록(주민번호:String, 성명:String)boolean
        +고객수정(주민번호:String, 성명:String)boolean
        +고객삭제(주민번호:String)boolean
        +고객조회(주민번호:String)user
    }

    class 주택정보 {
        -주소:String
        -주택가격:double
        -대출여부:boolean
        +주택등록(주소:String, 주택가격:double)boolean
        +주택수정(주소:String, 주택가격:double)boolean
        +주택삭제(주소:String)boolean
        +주택조회(주소:String)boolean
        +대출여부확인(주소:String)boolean
        +주택가격조회(주소:String)double
    }

    class 대출정보 {
        -대출ID:String
        -주민번호:String
        -주소:String
        -대출금액:double
        -상환금액:double
        -대출일:int
        -상환예정일:int
        -상환일:int
        +대출(주민번호:String, 주소:String, 대출금액:double, 대출일:int, 상환예정일:int)double
        +상환(주민번호:String, 주소:String, 상환일:int)double
        +연체확인(주민번호:String, 주소:String, 상환일:int)boolean
    }

    class 대출정보DAO {
        +대출(주민번호:String, 주소:String, 대출금액:double, 대출일:int, 상환예정일:int)double
        +상환(주민번호:String, 주소:String, 상환일:int)double
    }

    class HouseLoanUI {
        +대출신청()boolean
        +상환신청()boolean
    }

    대출정보 "0..*" --> "1" 고객정보 : 고객조회
    대출정보 "1" --> "1" 주택정보 : 주택조회
    HouseLoanUI ..> 대출정보 : 의존
    대출정보 ..> 대출정보DAO : DB저장