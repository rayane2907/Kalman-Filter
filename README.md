# Kalman Filter Tutorial

## 1. Introduction to Kalman Filter

The Kalman filter is an algorithm that uses a series of measurements observed over time, containing noise and other inaccuracies, to produce estimates of unknown variables that tend to be more accurate than those based on a single measurement alone.

## 2. Kalman Filter Equations

The Kalman filter consists of two steps: **predict** and **update**.

### Predict Step
1. **State prediction**: 
   \[
   \hat{x}_{k|k-1} = A \hat{x}_{k-1|k-1} + B u_k
   \]
2. **Covariance prediction**: 
   \[
   P_{k|k-1} = A P_{k-1|k-1} A^T + Q
   \]

### Update Step
3. **Kalman Gain**: 
   \[
   K_k = P_{k|k-1} H^T (H P_{k|k-1} H^T + R)^{-1}
   \]
4. **State update**: 
   \[
   \hat{x}_{k|k} = \hat{x}_{k|k-1} + K_k (z_k - H \hat{x}_{k|k-1})
   \]
5. **Covariance update**: 
   \[
   P_{k|k} = (I - K_k H) P_{k|k-1}
   \]

### Where:

- \(\hat{x}_{k|k-1}\) is the predicted state estimate.
- \(\hat{x}_{k|k}\) is the updated state estimate.
- \(P_{k|k-1}\) is the predicted covariance estimate.
- \(P_{k|k}\) is the updated covariance estimate.
- \(A\) is the state transition model.
- \(B\) is the control input model.
- \(u_k\) is the control vector.
- \(Q\) is the process noise covariance.
- \(H\) is the observation model.
- \(R\) is the observation noise covariance.
- \(z_k\) is the measurement at step \(k\).

## Running the Kalman Filter

Refer to the provided Python implementation in the `kalman_filter.py` file for a practical example of using the Kalman filter to track the position of a moving object. The example includes:

- Initializing the state, covariance, and other matrices.
- Performing the predict and update steps iteratively.
- Plotting the true position, noisy measurements, and Kalman filter estimates.
