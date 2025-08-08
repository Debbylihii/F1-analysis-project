import numpy as np
import pandas as pd

# 假設的旅遊數據
# ------------------
# 建立一個函式來生成模擬的旅遊數據
def generate_mock_travel_data(cities, start_date, end_date):
    """
    為指定的城市生成模擬的旅遊數據。

    cities: 賽事舉辦城市列表
    start_date, end_date: 數據生成的時間範圍
    """

    all_data = []
    # 產生一個時間序列，涵蓋賽季前後
    date_range = pd.date_range(start=start_date, end=end_date, freq='D')

    for city in cities:
        for date in date_range:
            # 隨機產生一個基礎銷售量，並增加一些隨機波動
            base_sales = np.random.randint(100, 500)
            sales = base_sales + np.random.randint(-50, 50)

            all_data.append({
                'city': city,
                'date': date,
                'sales': max(0, sales),  # 銷售量不能是負數
                'rating_avg': np.random.uniform(4.0, 5.0)  # 假設平均評價在 4.0 到 5.0 之間
            })

    return pd.DataFrame(all_data)


# 選擇幾個 F1 賽事城市進行模擬
f1_cities_to_mock = ['Sakhir', 'Jeddah', 'Melbourne', 'Suzuka']
start_of_season = '2024-02-01'
end_of_season = '2024-12-31'

# 生成模擬資料
travel_df = generate_mock_travel_data(f1_cities_to_mock, start_of_season, end_of_season)

print("--- 模擬旅遊數據 ---")
print(travel_df.head())
print(travel_df.info())

import numpy as np


# 假設的旅遊數據
# ------------------
# 建立一個函式來生成模擬的旅遊數據
def generate_mock_travel_data(cities, start_date, end_date):
    """
    為指定的城市生成模擬的旅遊數據。

    cities: 賽事舉辦城市列表
    start_date, end_date: 數據生成的時間範圍
    """

    all_data = []
    # 產生一個時間序列，涵蓋賽季前後
    date_range = pd.date_range(start=start_date, end=end_date, freq='D')

    for city in cities:
        for date in date_range:
            # 隨機產生一個基礎銷售量，並增加一些隨機波動
            base_sales = np.random.randint(100, 500)
            sales = base_sales + np.random.randint(-50, 50)

            all_data.append({
                'city': city,
                'date': date,
                'sales': max(0, sales),  # 銷售量不能是負數
                'rating_avg': np.random.uniform(4.0, 5.0)  # 假設平均評價在 4.0 到 5.0 之間
            })

    return pd.DataFrame(all_data)

# 選擇幾個 F1 賽事城市進行模擬
f1_cities_to_mock = ['Sakhir', 'Jeddah', 'Melbourne', 'Suzuka' , 'Singapore']
start_of_season = '2024-02-01'
end_of_season = '2024-12-31'

# 生成模擬資料
travel_df = generate_mock_travel_data(f1_cities_to_mock, start_of_season, end_of_season)

print("--- 模擬旅遊數據 ---")
print(travel_df.head())
print(travel_df.info())

# 確保 F1 DataFrame 已經存在，我們延用上次爬取的 f1_df
# f1_df = ... (假設已經成功爬取並清理)

# 將 f1_df 的賽事日期轉換為 datetime 格式，方便後續比較
f1_df['race_date'] = pd.to_datetime(f1_df['race_date'] + ', 2024')

# 創建一個新的 DataFrame 來標記比賽日期
# 讓旅遊數據能知道哪一天是比賽日
race_dates_df = f1_df[['city', 'race_date']].rename(columns={'race_date': 'race_day'})

# 將旅遊數據與比賽日期合併
# 使用 merge，根據城市和日期將賽事資訊加入旅遊數據中
merged_df = pd.merge(travel_df, race_dates_df, left_on=['city', 'date'], right_on=['city', 'race_day'], how='left')

# 創建一個新的欄位來標記是否為比賽日
merged_df['is_race_day'] = merged_df['race_day'].notna()

print("\n--- 整合後的數據 ---")
print(merged_df.head())
print(merged_df.info())
