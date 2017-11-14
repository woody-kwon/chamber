# 정신과 시간의 방(Hyperbolic Time Chamber) 정리

아래 양식 처럼 배운 것을 정리하면 됩니다. Readme.md 파일은 자유 형식입니다. 
Dictionary.md 파일은 알게 된 것과 모르는 것을 정리해서 정리하시면 됩니다.

이 프로젝트 오른쪽에 fork 버튼을 눌러 포크를 딴 후에 전체 내용은 지우시고 자신만의 컨텐츠를 채워가면 됩니다. [마크 다운 문법](https://gist.github.com/ihoneymon/652be052a0727ad59601)  

fork를 해 가시면 제가 주기적으로 확인해서 SDSACT 내의 Hyperbolic Time Chamber 프로젝트에 링크를 걸도록 하겠습니다.

SDS ACT 정신과 시간의 방 : https://github.com/SDSACT/hyperbolic_time_chamber 

## 1. Java8 in Action

### 1.1. 자바 8 개론

#### 새로 들어온 개념
- 스트림 API 
- behavior parameterization(함수를 매개변수로 던지기) 
- 병렬성과 공유 가변 데이터


#### 자바 함수
전달할 수 없는 구조체는 이급 시민이다. 자바8은 이급 시민을 일급 시민으로 바꿀 수 있다.

메쏘드를 람다로 하는 좋은 예
```Java
package chamber;

import java.io.File;
import java.io.FileFilter;

public class Chapter1 {
    public static void main(String args[]){
        hiddenfile();
        hiddenfileLambda();
    }

    public Chapter1() {
    }

    static void hiddenfile(){
        System.out.println("############ hiddenfile()" );
        File [] hiddenFiles = new File(".").listFiles(new FileFilter() {
            @Override
            public boolean accept(File pathname) {
                return pathname.isHidden();
            }
        });
        for(int i=0;i<hiddenFiles.length;i++){
            System.out.println(hiddenFiles[i].getAbsolutePath());
        }
    }
    static void hiddenfileLambda(){
        System.out.println("############ hiddenfileLambda()" );
        for (File file : new File(".").listFiles(File::isHidden)) {
            System.out.println(file.getAbsolutePath());
        }
    }
}
```

메쏘드 레퍼런스 :: (이 메소드를 값으로 사용하라는 의미)  - 기존 클래스의 메소드를 함수화 할 수 있다는 의미. 이 경우는 메소드를 일급값으로 사용함.

람다의 경우는 익명함수를 함수값으로 취급함. 람다의 예로 뭐가 좋을까 생각해 보면 필터 만큼 좋은 예제가 없음.



