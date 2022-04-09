````react

import PropTypes from "prop-types";

function FeedbackStats({ feedback }) {
  // Calculate Ratings Avg
  let average =  // we define a var and use it at return 
    feedback.reduce((acc, cur) => {
      return acc + cur.rating;
    }, 0) / feedback.length;

  average = average.toFixed(1).replace(/[.,]0$/, "");

  return (
    <div className="feedback-stats">
      <h4>{feedback.length} Reviews</h4>
      <h4>Average Rating : {isNaN(average) ? 0 : average}</h4>
    </div>
  );
}

FeedbackStats.propTypes = {
  feedback: PropTypes.array.isRequired,
};

export default FeedbackStats;


````

![Screenshot_16](C:\Users\erenc\Desktop\React Notlarım\Feedback UI Notes\Screenshot_16.png)