# linking-island-
# python
n개의 섬 사이에 다리를 건설하는 비용(costs)이 주어질 때, 최소의 비용으로 모든 섬이 서로 통행 가능하도록 만들 때 필요한 최소 비용을 return 하도록 solution을 완성하세요. 임의의 i에 대해, costs[i][0] 와 costs[i] [1]에는 다리가 연결되는 두 섬의 번호가 들어있고, costs[i] [2]에는 이 두 섬을 연결하는 다리를 건설할 때 드는 비용입니다. 연결할수 없는 섬은 없다.

def solution(n, costs): #kruskal 알고리즘
    answer = 0
    costs.sort(key=lambda x : x[2]) #비용을 오름차순으로 정렬
    array=set([costs[0][0]]) #집합으로 만들기
    while len(array)!=n: #연결할수 없는 섬은 주어지지 않음
        for a in costs:
            if a[0] in array and a[1] in array:
                continue #두섬이 낮은비용이면 패스
            if a[0] in array or a[1] in array: #두섬중 하나가 연결되지 않았다면 비용추가
                array.update([a[0],a[1]]) #집합에 섬들 추가
                answer+=a[2] 
                break
    return answer
n=4
costs=[[0,1,1],[0,2,2],[1,2,5],[1,3,1],[2,3,8]]
b=solution(n, costs)
print(b)

-->결과: 4(최소비용)
