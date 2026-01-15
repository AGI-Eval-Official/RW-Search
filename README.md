<p align="right">
  <a href="README_CN.md">简体中文</a> | <a href="README.md">English</a>
</p>

# RW-Search
**RWSearch: A High-Order Logic and Real-World Search Evaluation Benchmark for Agents.**

RWSearch is a rigorous benchmark designed to deeply evaluate the cognitive depth, multi-dimensional retrieval, long-chain reasoning, and precise computational execution capabilities of LLMs and their Agents within a Chinese linguistic context.

## 💡 Core Characteristics of the Benchmark
🎯 RWSearch consists of 200 real-world, complex questions crafted by domain experts, each with a unique objective answer.

🎯 RWSearch adopts "Anchoring to Reality" as its core design philosophy, placing Agents in the complex and dynamic real-world internet ecosystem. The task design balances forward retrieval and reverse reasoning, incorporating extensive numerical clarification, statistical computation, and dynamic comparison, with a strong emphasis on time-sensitive information and long logical chains.

### Deep Mapping of Dynamic Real-World Evolution 
**Core Description:** The benchmark focuses on time-sensitive and segmented scenarios within a globalized vision, requiring Agents to capture transient trends in fluid information like human experts.
- **Interplay of Globalization and Localization:** Tasks cover international topics (e.g., Billboard charts, NBA events, Nobel Prizes) as well as intricate Chinese local affairs (e.g., passenger volume statistics, livestock breeds, employment supply and demand).
- **Information Integration Across Multi-dimensional Verticals:** A single query can span multiple domains such as engineering, sports, and education. The associative relationships across various domains encompass diverse types such as interpersonal relationships, commercial affiliations, and spatio-temporal calculus. This tests the model's entity alignment and information integration capabilities.
- **High Timeliness and Anti-Memorization Design:** Content covers dynamic facts from late 2024 to 2025, restricting the model's reliance on "pre-training memory" and forcing real-time browsing and information verification.

**Statistical Distribution by Domain:** The benchmark covers eight major domains, reflecting real-world scenarios of in-depth internet research. Each task may involve multiple vertical domains; for statistical purposes here, the categorization is based on the vertical to which the final question belongs.

| Domain                   | Num. | Percentage |
|--------------------------|------|------------|
| Media & Entertainment    | 54   | 27%        |
| Public Affairs           | 34   | 17%        |
| Production & Consumption | 28   | 14%        |
| Literature & Art         | 27   | 14%        |
| Economy & Business       | 17   | 9%         |
| Science & Technology     | 15   | 8%         |
| Sports                   | 14   | 7%         |
| Politics & Law           | 11   | 6%         |
| Total                    | 200  | 100%       |

- **Freshness:** The "Freshness" is defined by the latest year of information involved in a task. 60% of the tasks involve information from 2025.

| Freshness      | Num. | Percentage |
|----------------|------|------------|
| 2025           | 119  | 60%        |
| 2024           | 48   | 24%        |
| 2023 and prior | 33   | 17%        |

### Decision-Making Based on Numerical Clarification and Comparison 

**Core Feature:** Agents must utilize filtering, sorting, and calculation to identify a target within a candidate set before proceeding to the next search step or final answer.
- **Multi-dimensional Comparison for Uniqueness:** Queries often include quantitative instructions such as "ranked Xth," "maximum/minimum/difference," or "yoy increase," combined to form complex constraints.
- **High-Precision Mathematical Execution:** Agents are required to transform web data into structured numerical values and perform precise operations like "calendar day difference" or "rounded ratios".

**Example Task:**
- **Task:** 截至2025年6月，获得最多的大满贯单打冠军的运动员在其职业生涯中与获得大满贯单打冠军数排名第二的男子运动员交手过多少次？（仅统计官方正规赛事）
- **Execution Difficulty:** The Agent must retrieve Grand Slam title counts, rank the athletes to identify "No. 1" and "No. 2," and then retrieve their head-to-head records. Any data omission or calculation error will lead to entity deviation and an incorrect answer.

## ⚖️ Comparative Advantages over Existing Benchmarks

🎯 RWSearch closely mirrors real-world user queries, shifting the evaluation focus from "parsing complex queries and multi-step reasoning" to "answer search capability in noisy real-world scenarios," which better reflects the genuine needs of today's users.

🎯 RWSearch ensures high reproducibility and scientific cross-model comparison by carefully selecting "time-locked" facts, addressing the issue of answer invalidation over time that plagues similar benchmarks.

### High Semantic Clarity and Rigorous Instructions
**Industry Pain Point:** Many datasets suffer from subjective or vague constraints and unclear temporal/subject references, leading to model failures caused by comprehension bias rather than lack of capability.

**RWSearch Solution:** Provides high-clarity constraint instructions, strictly limiting outputs to specific formats like "numbers," "dates," or "specific entities". 
- For numerical or date-time answers, constraints are imposed on units, decimal formats, algebraic signs, and temporal formats; for entity-based answers, constraints extend to language, full names versus abbreviations, and the granularity of geographical divisions.
- For ambiguous concepts, it provides clear boundaries (e.g., providing both original and translated names for overseas entities; specifying that skyscraper statistics exclude uncompleted buildings and use total height).

### Noise Opposition in Real Search Ecosystems 
**Industry Pain Point:** Many datasets rely on "clean" sources like Wikipedia, which lack the complexity of real-world research involving similar terms or outdated information.

**RWSearch Solution:** Focuses on data hidden in government bulletins, annual reports, and industry papers. It introduces "near-synonym interference" and "tier traps" 
- Agents must identify the underlying definitional discrepancies between technical terms, rather than performing blind data extraction.（e.g.,distinguishing between "permanent population" vs. "year-end population"

- Agents need to extract data from complex statistical charts, clean and aggregate data across multiple years, and avoid interference from datasets that are similar in nature but differ in scope.

### Temporal Stability and Objective Ground Truth Uniqueness
**Industry Pain Point:** Many datasets suffer from the "moving target" problem, where real-world changes cause answers to become invalid or multi-valued.

**RWSearch Solution:** Adheres to the principle of "dynamic process, static result", ensuring that the answers remain unique and immutable.
- It anchors tasks to facts with physical or logical certainty (e.g., published statistical reports or specific exhibition dates). 
- It sets deadlines for information, requiring Agents to proactively filter out-of-date data or invalid conjectures, anchoring to the latest official releases while aligning with specific cutoff time requirements.

## 📚 Examples

<table>
  <tr>
    <th>Domain</th>
    <th>Problem</th>
    <th>Correct Answer</th>
  </tr>
  <tr>
    <td nowrap>体育运动</td>
    <td>2023-2024 赛季 NBA 常规赛中，尼古拉・约基奇在最后10场比赛中的三分球命中率（百分比，四舍五入保留一位小数）是多少？</td>
    <td nowrap>39.4%</td>
  </tr>
  <tr>
    <td nowrap>公共事务</td>
    <td>2020-2024年5年间，中国民航机场旅客吞吐量累积排名第五高的机场，在这5年的累计旅客吞吐量是多少（单位：亿人次，四舍五入保留2位小数）</td>
    <td nowrap>1.86亿人次</td>
  </tr>
  <tr>
    <td nowrap>生产消费</td>
    <td>2024年3月到12月期间，社会消费品零售总额同比增长最快的月份，比增长最慢的月份，多增长了几个百分点？</td>
    <td nowrap>2.8个</td>
  </tr>
  <tr>
    <td nowrap>经济商业</td>
    <td>2020年至2024年期间，小米集团总收入最低那年的年度经营利润是多少（四舍五入到个位，人民币，单位：亿元）？</td>
    <td nowrap>240亿元</td>
  </tr>
  <tr>
    <td nowrap>影音娱乐</td>
    <td>五月天"5525 回到那一天"主题演唱会的第66场是在哪个场馆举办的？</td>
    <td nowrap>新加坡国家体育场</td>
  </tr>
</table>

## 🏆 LeaderBoard
### Models (w/o context management)
<table>
  <tr>
    <th>Class</th>
    <th>Model</th>
    <th>Score</th>
  </tr>
  <tr>
    <td rowspan="3">Proprietary</td>
    <td>gpt-5.2-thinking (xhigh)</td>
    <td><b>82.0</b></td>
  </tr>
  <tr>
    <td>gemini-3-pro-preview</td>
    <td>74.5</td>
  </tr>
  <tr>
    <td>claude-opus-4.5</td>
    <td>75.5</td>
  </tr>
  <tr>
    <td rowspan="5">Open Source</td>
    <td>longcat-flash-thinking-2601</td>
    <td><b>79.5</b></td>
  </tr>
  <tr>
    <td>deepseek-v3.2-reasoner</td>
    <td>74.0</td>
  </tr>
  <tr>
    <td>glm-4.7-thinking</td>
    <td>69.0</td>
  </tr>
  <tr>
    <td>kimi-k2-thinking</td>
    <td>63.0</td>
  </tr>
  <tr>
    <td>qwen3-235b-a22b-thinking-2507</td>
    <td>20.5</td>
  </tr>
  <tr>
    <td colspan="3" align="center"><i>More model results coming soon...</i></td>
  </tr>
</table>

> **Bold** indicates best performance among similar models.

### Search Agents (w/ context management)
Coming soon...

## 📖 Citation

If you use the code or resources from this project, please cite as follows:

```bibtex
@misc{rwsearch2026,
  author       = {Zhu, Mingyang and Liu, Wei and others},
  title        = {RW-Search: A High-Order Logic and Real-World Search Evaluation Benchmark for Agents},
  year         = {2026},
  url          = {https://github.com/AGI-Eval-Official/RW-Search}
}
```

## ☁️ Contact

If you have any questions, please contact us via:

Author Email: zhumingyang09@meituan.com, liuwei304@meituan.com