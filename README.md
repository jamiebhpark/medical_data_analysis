### 의료 데이터 분석 및 시각화 도구

### 1. 프로젝트 개요

**프로젝트 이름**: 의료 데이터 분석 및 시각화 도구

**목적**: 의료 데이터를 분석하고 시각화하여 사용자가 유용한 인사이트를 얻을 수 있도록 하는 도구를 개발합니다.

**주요 기능**:

- 의료 데이터 불러오기 (예: CSV 파일)
- 데이터 전처리 및 정리
- 다양한 형태의 데이터 분석 (예: 통계 분석, 트렌드 분석)
- 데이터 시각화 (예: 라인 차트, 바 차트, 히스토그램)
- 결과 시각화 저장

**기술 스택**: Python, Pandas, Matplotlib, Seaborn

---

### 3. 디렉토리 구조 설정

```bash
medical_data_analysis/
│
├── data/
│   └── medical_data.csv  # 예제 데이터 파일
│
├── src/
│   └── analyze.py  # 데이터 분석 및 시각화 코드
│
└── venv/  # 가상 환경 디렉토리
```

1. **디렉토리 생성**:
    - PyCharm의 프로젝트 창에서 프로젝트 루트 디렉토리를 우클릭하고, `New` -> `Directory`를 선택하여 `data`와 `src` 디렉토리를 만듭니다.
2. **CSV 파일 생성**:
    - `data` 디렉토리를 우클릭하고, `New` -> `File`을 선택하여 `medical_data.csv` 파일을 생성합니다.
    - 다음과 같은 데이터를 예제로 추가합니다:
        
        ```
        csv코드 복사
        patient_id,age,weight,height,blood_pressure,cholesterol,glucose_level
        1,25,70,175,120/80,190,85
        2,45,85,165,130/85,210,90
        3,35,78,180,125/82,200,88
        4,60,90,160,140/90,220,95
        5,50,82,170,135/88,215,92
        
        ```
        
3. **Python 파일 생성**:
    - `src` 디렉토리를 우클릭하고, `New` -> `Python File`을 선택하여 `analyze.py` 파일을 생성합니다.

---

### 4. 코드 작성

**analyze.py**:

```python
python코드 복사
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

def load_data(file_path):
    """
    Load medical data from a CSV file.
    """
    return pd.read_csv(file_path)

def preprocess_data(data):
    """
    Preprocess the data: clean and format the data for analysis.
    """
    # Split blood pressure into systolic and diastolic
    bp_split = data['blood_pressure'].str.split('/', expand=True)
    data['systolic_bp'] = pd.to_numeric(bp_split[0])
    data['diastolic_bp'] = pd.to_numeric(bp_split[1])

    # Drop the original blood_pressure column
    data = data.drop(columns=['blood_pressure'])

    return data

def visualize_data(data):
    """
    Visualize medical data using various plots.
    """
    plt.figure(figsize=(12, 6))

    # Histogram for age
    plt.subplot(1, 2, 1)
    sns.histplot(data['age'], kde=True, bins=10)
    plt.title('Age Distribution')

    # Scatter plot for height vs weight
    plt.subplot(1, 2, 2)
    sns.scatterplot(data=data, x='height', y='weight', hue='age', palette='coolwarm')
    plt.title('Height vs Weight')

    plt.tight_layout()
    plt.savefig('data_visualization.png')
    plt.show()

if __name__ == "__main__":
    # Load the data
    data = load_data('../data/medical_data.csv')

    # Preprocess the data
    data = preprocess_data(data)

    # Visualize the data
    visualize_data(data)

```

---

### 5. 코드 실행

1. **코드 실행**:
    - `analyze.py` 파일을 열고, PyCharm의 상단에 있는 `Run` 버튼을 클릭하여 코드를 실행합니다.
    - 또는, `analyze.py` 파일을 우클릭하고, `Run 'analyze'`를 선택합니다.

---

### 6. 결과 확인

1. **결과 이미지 확인**:
    - 코드 실행 후, 프로젝트 루트 디렉토리에 `data_visualization.png` 파일이 생성되었는지 확인합니다.
    - `data_visualization.png` 파일을 열어 시각화된 그래프를 확인합니다.
    
    ![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/f9f35de7-0091-4a79-819a-501ef9435828/6918e7b7-6acb-44c6-bbca-02a9e5c169c2/Untitled.png)
    

---

### 7. 프로젝트 요약 및 결론

**프로젝트 요약**:
이 프로젝트는 의료 데이터를 분석하고 시각화하여 사용자가 유용한 인사이트를 얻을 수 있도록 하는 간단한 도구를 개발하였습니다. Pandas를 사용하여 데이터를 로드하고 전처리하였으며, Matplotlib과 Seaborn을 사용하여 데이터를 시각화하였습니다.

**결론**:
이 프로젝트를 통해 데이터 분석 및 시각화 기술과 관련된 기본기를 향상시킬 수 있었으며, 의료 데이터를 효과적으로 분석하고 시각화하는 방법을 배울 수 있었습니다.
