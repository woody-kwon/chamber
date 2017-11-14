## Java8 in Action을 여행하는 왕초보를 위한 안내서

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



