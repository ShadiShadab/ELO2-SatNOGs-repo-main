# 📝 Project Reflection & Retrospective

## 🚀 The Journey

This capstone project has been an incredible journey of discovery, problem-solving, and growth. What began as a simple idea to apply machine learning to satellite observations transformed into a comprehensive project with real-world impact for the SatNOGS community.

## ⚡ The Biggest Challenge: Data Acquisition

The most significant hurdle came right at the beginning. The initial dataset I received was in CSV format and was essentially unusable - poorly structured, incomplete, and lacking critical relationships. For weeks, I struggled to make sense of the data, feeling stuck before I could even begin the real work.

Then came the breakthrough: a colleague provided access to the **original SQL database** - a massive 22GB repository containing the complete SatNOGS observation history. Suddenly, I went from wrestling with messy CSVs to querying a rich, relational database with 12.5+ million observations. This was the turning point that made everything possible.

## 🔄 From Chaos to Clarity

Working with the SQL database taught me invaluable lessons:
1. **Raw data is messy, but structure brings clarity** - The SQL schema revealed relationships I never would have seen in flat files
2. **Big data requires smart sampling** - I learned to extract meaningful samples (578K observations) without losing statistical significance
3. **Database skills are essential** - Writing efficient queries became as important as writing Python code

## 🧠 Key Learnings

### Technical Growth
- **Data Leakage Detection**: Finding and fixing the perfect predictor issue taught me that "too good to be true" results usually are
- **Temporal Validation**: Learning to split data by time instead of randomly was crucial for realistic performance evaluation
- **Model Interpretability**: Discovering that business rules matter more than black-box accuracy scores
- **Scalable ML**: Working with large datasets forced me to optimize memory usage and processing pipelines

### Professional Development
- **Persistence Pays**: When the first dataset failed, I didn't give up - I sought better alternatives
- **Communication is Key**: Translating technical ML results into actionable business rules for operators
- **Project Scope Management**: Starting with a huge 22GB database and narrowing down to a focused, impactful project

## 💡 Most Valuable Insights

1. **The simplest solution is often the best** - Random Forest outperformed more complex neural networks while being more interpretable
2. **Domain knowledge transforms data** - Understanding satellite communication made feature engineering meaningful
3. **Impact matters more than metrics** - A 76.8% reduction in failed observations is more valuable than any ROC-AUC score
4. **Community contribution has real value** - Creating something that helps 600+ volunteer operators feels incredibly rewarding

## 🎓 MIT Program Impact

This project exemplified the MIT Emerging Talent Program's philosophy: combining technical rigor with real-world application. The structured approach - from domain study to data preparation, exploration, analysis, and communication - provided a framework I'll carry throughout my career.

## 🌟 Final Thoughts

Looking back, the journey from that initial unusable CSV to a complete ML system with a professional dashboard feels surreal. The challenges - especially the data acquisition struggle - taught me resilience. The breakthroughs - discovering the SQL database, fixing data leakage, achieving 94.6% ROC-AUC - taught me that persistence and methodical problem-solving lead to success.

Most importantly, I learned that **technical projects can create tangible human impact**. Every percentage point improvement in success rate means less wasted time for volunteers, more scientific data collected, and a more efficient satellite tracking network. That's the real measure of success.

This project wasn't just about building a machine learning model; it was about solving a real problem for a real community. And that's the most valuable lesson of all.

---

**Shadi Shadabshoar**  
*MIT Emerging Talent Program in Computer and Data Science*  
*December 2025*
